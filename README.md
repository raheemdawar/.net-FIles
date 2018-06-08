# .net-FIles
using System;
using System.Collections.Generic;
using System.Linq;

using DbInteraction.DB;
namespace DbInteraction
{
    class Program
    {
        private static GuideLineEntities _db = new GuideLineEntities();
        static void Main(string[] args)
        {
            User userObject = new User();
            Console.WriteLine("Enter User Name");
            userObject.User_name = Console.ReadLine();
            Console.WriteLine("Enter User Email" +
                "");
            userObject.User_email = Console.ReadLine();
            _db.Users.Add(userObject);

            _db.SaveChanges();
            Console.WriteLine("Congratulation mr. Waqas ,Your First Entry to Database");
            List<User> listOfUsers = _db.Users.ToList();
            for(int i=0;i<listOfUsers.Count;i++)
            {
                Console.WriteLine(listOfUsers[i].User_name);
                Console.WriteLine(listOfUsers[i].User_email);
                if(i==0)
                {
                    _db.Users.Remove(listOfUsers[0]);
                    _db.SaveChanges();
                }
            }
            listOfUsers = _db.Users.ToList();
            for (int i = 0; i < listOfUsers.Count; i++)
            {
                Console.WriteLine(listOfUsers[i].User_name);
                Console.WriteLine(listOfUsers[i].User_email);
             
            }


            Console.ReadLine();
        }
    }
}
