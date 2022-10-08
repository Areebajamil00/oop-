using System;

namespace ConsoleApp2
{
    interface Customer //i'm using interface class because there is no any shared functionality  only we need initialization
    {                 //because of only definition I made interface class 
        public bool IsTaxPayer    //setter and getter
        {
            get; set;
        }
        public int Units
        {
            get;
            set;
        }

        public float calculateBill(int units);//function definition

    }
    class Residential : Customer//inheritance
    {

        public bool IsTaxPayer { get; set; }//getter setter
        public int Units { get; set; }

        public float calculateBill(int units)//bill calculation
        {
            int totalAmount = 0;
            if (IsTaxPayer == false) //if he/she is not tax payer do this
            {
                if (units <= 100)
                {
                    totalAmount = units * 5;
                }
                else if (units > 100 && units <= 200)
                {
                    totalAmount = (100 * 5) +
                           (units - 100) * 17;
                }
                else if (units > 200 && units <= 500)
                {
                    totalAmount = (100 * 5) +
                           (100 * 17) +
                           (units - 200) * 23;
                }
                else if (units > 500)
                {
                    totalAmount = (100 * 5) + (100 * 17) + (100 * 23) + (units - 300) * 69;
                }

            }
            else //if he/she is taxpayer
            {
                if (units <= 100) //all cases are same with not tax payer only third is differenet case (units > 200 && units <= 500)
                {
                    totalAmount = units * 5;
                }
                else if (units > 100 && units <= 200)
                {
                    totalAmount = (100 * 5) +
                           (units - 100) * 17;
                }
                else if (units > 200 && units <= 500) //for third xondition if he/she is not tax payer then use the previous slab;
                {
                    totalAmount = (100 * 5) +
                           (100 * 17) +
                           (units - 200) * 17;
                }
                else if (units > 500)
                {
                    totalAmount = (100 * 5) + (100 * 17) + (100 * 17) + (units - 300) * 69;
                }
                Console.WriteLine("residence");
              //  Console.WriteLine(totalAmount);
            }
            float tax = 0.13f;//tax
     
           // Console.WriteLine(tax);
            float amount = (tax) * totalAmount;//tax calculation and return amount
            return amount;
        }
    }
    class Commercial : Customer
    {
        public bool IsTaxPayer { get; set; }//getter setter
        public int Units { get; set; }

        public float calculateBill(int units)
        {
            int totalAmount = 0;
            if (IsTaxPayer == false) //if not taxpayer
            {
                if (units <= 100)
                {
                    totalAmount = units * 8;
                }
                else if (units > 100 && units <= 200)
                {
                    totalAmount = (100 * 8) +
                           (units - 100) * 21;
                }
                else if (units > 200 && units <= 500)
                {
                    totalAmount = (100 * 8) +
                           (100 * 21) +
                           (units - 200) * 23;
                }
                else if (units > 500)
                {
                    totalAmount = (100 * 8) + (100 * 21) + (100 * 23) + (units - 300) * 79;
                }

            }
            else //if tax payer
            {
                if (units <= 100)
                {
                    totalAmount = units * 8;
                }
                else if (units > 100 && units <= 200)
                {
                    totalAmount = (100 * 8) +
                           (units - 100) * 21;
                }
                else if (units > 200 && units <= 500)//third condition is 
                                                     //different only when he/she is tax payer same slab will use as previous
                {
                    totalAmount = (100 * 8) +
                           (100 * 21) +
                           (units - 200) * 21;
                }
                else if (units > 500)
                {
                    totalAmount = (100 * 8) + (100 * 21) + (100 * 21) + (units - 300) * 79;
                }

            }
            float tax = 0.17f; //tax calculation
            //Console.WriteLine(tax);
            float amount = (tax) * totalAmount;
            return amount;
        }
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Enter the units:");//user input
                string str = Console.ReadLine();
                int units = Int32.Parse(str);
                //Console.WriteLine("Customer is tax payer or not :");
                //string str1 = Console.ReadLine();
                Customer customer1 = new Residential();//making object of main class and give memory to child class
                Customer customer2 = new Commercial();//making object of main class and give memory to child class
                customer1.IsTaxPayer = false;//set value of bool variable
               // customer1.Units = units;
                float unit = customer1.calculateBill(units);//store value of unit which return from calculate function
                Console.WriteLine("For residential the total bill is:"+unit);
               float  unit1 = customer2.calculateBill(units);
                Console.WriteLine("For commercial the total bill is:" + unit1);
                Console.ReadLine();
                //customer2.IsTaxPayer = true;
                //customer2.Units = units;


            }
        }
    }
}

