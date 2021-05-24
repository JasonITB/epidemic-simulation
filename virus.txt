import java.util.*;
public class virus {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("population");
        int population = sc.nextInt();
        System.out.println("people infected on day one");
        int infected = sc.nextInt();
        System.out.println("time untill one is recovered");
        int timetorec = sc.nextInt();
        System.out.println("infection probability 0.XX");
        double prob = sc.nextDouble();
        System.out.println("meet how many people a day");
        int meet = sc.nextInt();
        System.out.println("simulation time");
        int simtime = sc.nextInt();
        System.out.println("newborn");
        int newborn = sc.nextInt();
        int day = 1;
        int[] rec;
        rec = new int[simtime];
        rec[1] = infected;
        int immune = 0;
        day++;

        int totalinfect = infected;

        System.out.println("day: "+1+" infeced: "+infected);

        while(day<simtime){ 

            if(infected <= 5){infected = 10;}

            population = population + newborn;
            int newinfected = day(population,infected,timetorec,meet,prob,day,immune);
            infected = infected + newinfected;
            rec[day] = newinfected;
            if(day >=timetorec){infected = infected - rec[day-timetorec];
            immune = immune + rec[day-timetorec];}


            System.out.println("day: "+day+" infeced: "+infected+" immune:"+ immune);
            System.out.println(infected);
            if(infected >= population){
                System.out.print("|unprotected| "); //THIS LINE CAN BE COMMENTED OUT. RESULTS AFTER UNPROTECTED WILL NOT BE ACCURATE
            }
            day++;
            totalinfect = totalinfect+newinfected;

        }
        System.out.println("total infected: " + totalinfect); //CUSTOMIZE THIS LINE FOR DIFFENT DATA AND FORMATING

        sc.close();

        
    }

    public static int day(int population, int infected, int timetorec, int meet, double prob, int day,int immune){
        int contacts = infected*meet;
        int newInfected = 0;
        double immuneprecent = (immune+infected)/population;

        for (int m = 1; m <= contacts; m++){
            double testnr = Math.random();
            double test = Math.round(testnr*100.0)/100.0;
            if(test <= prob){
                double testnr2 = Math.random();
                double test2 = Math.round(testnr2*100.0)/100.0;
                if(test2 >= immuneprecent){
                    newInfected++;
                }
            }
        }
        return newInfected;
    }

    
}

// import java.util.*;
// public class virus{
//     public static void main(String[] args) {
//         Scanner sc = new Scanner(System.in);
//         //population stats
//         long population; //#total alive people
//         long susceptible; //#of people suseptibal
//         long infected; //#of people infected
//         long immune; //#of people immune
//         //virus stats
//         int timetorec; //time for one to recover
//         int startwith; //starting population of the virus on day 1
//         double infectionprobability; //chance of infecting someone you meet
//         int meet;  //#of people one meets a day
//         //simulation stats
//         int simulationtime;
//         int day;

//         //virus stats
//         System.out.println("time to recover: ");
//         timetorec = sc.nextInt(); //time for one to recover
//         System.out.println("start with: ");
//         startwith = sc.nextInt(); //starting population of the virus on day 1
//         System.out.println("infection probability 0.xx: ");
//         infectionprobability = sc.nextDouble(); //chance of infecting someone you meet
//         System.out.println("meets per day: ");
//         meet = sc.nextInt();  //#of people one meets a day
//         //simulation stats
//         System.out.println("simtime: ");
//         simulationtime = sc.nextInt();
//         day = 1;
//         //popoulation stats
//         System.out.println("starting population: ");
//         population = sc.nextLong(); //#total alive people
//         susceptible = population; //#of people suseptibal
//         infected = startwith; //#of people infected
//         immune = 0; //#of people immune

//         Long[] rec;
//         rec = new Long[simulationtime];

//         while (day<=simulationtime){
//             Long newinfected = randomnewinfected(infected, infectionprobability, meet, susceptible, population);
//             if(day>timetorec){
//                 infected = infected - rec[day-timetorec];
//                 immune = immune + rec[day-timetorec];
//             }
//             rec[day] = newinfected;
//             infected = infected + newinfected;
//             //new births and deaths

//             susceptible = population - immune - infected;
//             System.out.println(infected + "     " + immune);
//             day++;
//         }

//         sc.close();
//     }

//     public static Long randomnewinfected(Long infected, Double infectionprobability, int meet, Long susceptible, Long population){
//         Long meetnum = infected*meet;
//         double suspercent = susceptible/population;
//         double round = meetnum*suspercent;
//         Long meetsus = (long) round;
//         Long newinfected = (long) 0;
//         for(Long encounter = (long) 0; encounter < meetsus; encounter++){
//             if (Math.random()<= infectionprobability){
//                 newinfected++;
//             }
//         }
//         return newinfected;
//     }
// }

// import java.util.*;
// public class virus {

//     public static void main(String[] args) {
//         Scanner sc = new Scanner(System.in);
//         System.out.println("population");
//         int population = sc.nextInt();
//         System.out.println("people infected on day one");
//         int infected = sc.nextInt();
//         System.out.println("time untill one is recovered");
//         int timetorec = sc.nextInt();
//         System.out.println("infection probability 0.XX");
//         double prob = sc.nextDouble();
//         System.out.println("meet how many people a day");
//         int meet = sc.nextInt();
//         System.out.println("simulation time");
//         int simtime = sc.nextInt();
//         int day = 1;
//         int[] rec;
//         rec = new int[simtime];
//         rec[1] = infected;
//         int immune = 0;
//         day++;

//         int totalinfect = infected;

//         System.out.println("day: "+day+" infeced: "+infected);

//         while(day<simtime){

//             int newinfected = day(population,infected,timetorec,meet,prob,day,immune);
//             infected = infected + newinfected;
//             rec[day] = newinfected;
//             if(day >=timetorec){infected = infected - rec[day-timetorec];
//             immune = immune + rec[day-timetorec];}


//             System.out.println("day: "+day+" infeced: "+infected+" immune:"+ immune);
//             if(infected >= population){
//                 System.out.print("|unprotected| ");
//             }
//             day++;
//             totalinfect = totalinfect+newinfected;


//         }
//         System.out.println("total infected: " + totalinfect);

//         sc.close();

        
//     }

//     public static int day(int population, int infected, int timetorec, int meet, double prob, int day,int immune){
//         int contacts = infected*meet;
//         int newInfected = 0;
//         double immuneprecent = (immune+infected)/population;

//         for (int m = 1; m <= contacts; m++){
//             double testnr = Math.random();
//             double test = Math.round(testnr*100.0)/100.0;
//             if(test <= prob){
//                 double testnr2 = Math.random();
//                 double test2 = Math.round(testnr2*100.0)/100.0;
//                 if(test2 >= immuneprecent){
//                     newInfected++;
//                 }
//             }
//         }
//         return newInfected;
//     }

    // public static String death(int population, int immune, int infected){
    //     double testnr = Math.random();
    //     double test = Math.round(testnr*100.0)/100.0;

    //     int immuneprob = immune/population;

    //     int infectedprob = infected/population;


        
    // }

    
// }

/* version 3 ----- attept at births and deaths not functinal
import java.util.*;
public class virus {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("population: recomended number > 125000");
        int population = sc.nextInt();
        System.out.println("people infected on day one");
        int infected = sc.nextInt();
        System.out.println("time untill one is recovered");
        int timetorec = sc.nextInt();
        System.out.println("infection probability 0.XX");
        double prob = sc.nextDouble();
        System.out.println("meet how many people a day");
        int meet = sc.nextInt();
        System.out.println("how many people will be born a day: reccomended number: " + population/12500);
        int born = sc.nextInt();
        // System.out.println("how many people will die: recomended number: " + born/2.5);
        // int death = sc.nextInt();
        System.out.println("simulation time");
        int simtime = sc.nextInt();
        int day = 1;
        int[] rec;
        rec = new int[simtime];
        rec[1] = infected;
        int immune = 0;
        day++;

        // String deathtype = "";

        int totalinfect = infected;

        // System.out.println("day: 1"+" infeced: "+infected);
        System.out.println(infected);

        while(day<simtime){

            int newinfected = day(population,infected,timetorec,meet,prob,day,immune);
            infected = infected + newinfected;
            rec[day] = newinfected;
            if(day >=timetorec){infected = infected - rec[day-timetorec];
            immune = immune + rec[day-timetorec];}

            population = population + born;

            // System.out.println("day: "+day+" infeced: "+infected+" immune:"+ immune+" population: " + population+ " suseptibal: "+(population-immune-infected));
            // if(infected >= population){
            //     System.out.print("|unprotected| ");
            // }
            System.out.println(infected);

            day++;
            totalinfect = totalinfect+newinfected;


        }
        System.out.println("total infected: " + totalinfect);

        sc.close();

        
    }

    public static int day(int population, int infected, int timetorec, int meet, double prob, int day,int immune){
        int contacts = infected*meet;
        int newInfected = 0;
        double immuneprecent = (immune+infected)/population;

        for (int m = 1; m <= contacts; m++){
            double testnr = Math.random();
            double test = Math.round(testnr*100.0)/100.0;
            if(test <= prob){
                double testnr2 = Math.random();
                double test2 = Math.round(testnr2*100.0)/100.0;
                if(test2 >= immuneprecent){
                    newInfected++;
                }
            }
        }
        return newInfected;
    }

    // public static String randomtype(int population, int infected, int immune, Double test){
    //     //1 = uninfected 2 = immune 3 = infected
    //     double infectedprob = 999;
    //     double immuneprob = 999;

    //     String re = " ";
        
    //     if (immune > 0 && infected > 0){
    //         infectedprob = infected/population;
    //         immuneprob = immune/population+infectedprob;
    //         if (0 <= test && test < infectedprob){
    //             return "infected";
    //         }else if (infectedprob <= test && test < immuneprob){
    //             return "immune";
    //         }
    //         else{
    //             re = "susceptible";
    //         }
    //     }

    //     if (immune <= 0 && infected > 0){
    //         immuneprob = immune/population;
    //         if (0 <= test && test < immuneprob){
    //             return "immune";
    //         }
    //         else{
    //             re = "susceptible";
    //         }
    //     }

    //     if (infected <= 0 && immune > 0){
    //         infectedprob = infected/population;
    //         if (0 <= test && test < infectedprob){
    //             return "infected";
    //         }
    //         else{
    //             re = "susceptible";
    //         }
    //     }
    //     return " ";
    // }

    
}

*/



/* version 2, herd immunity and immunity, dosent condider people dieing and new births
import java.util.*;
public class virus {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("population");
        int population = sc.nextInt();
        System.out.println("people infected on day one");
        int infected = sc.nextInt();
        System.out.println("time untill one is recovered");
        int timetorec = sc.nextInt();
        System.out.println("infection probability 0.XX");
        double prob = sc.nextDouble();
        System.out.println("meet how many people a day");
        int meet = sc.nextInt();
        System.out.println("simulation time");
        int simtime = sc.nextInt();
        int day = 1;
        int[] rec;
        rec = new int[simtime];
        rec[1] = infected;
        int immune = 0;
        day++;

        int totalinfect = infected;

        System.out.println("day: "+day+" infeced: "+infected);

        while(day<simtime){

            int newinfected = day(population,infected,timetorec,meet,prob,day,immune);
            infected = infected + newinfected;
            rec[day] = newinfected;
            if(day >=timetorec){infected = infected - rec[day-timetorec];
            immune = immune + rec[day-timetorec];}


            System.out.println("day: "+day+" infeced: "+infected+" immune:"+ immune);
            if(infected >= population){
                System.out.print("|unprotected| ");
            }
            day++;
            totalinfect = totalinfect+newinfected;


        }
        System.out.println("total infected: " + totalinfect);

        sc.close();

        
    }

    public static int day(int population, int infected, int timetorec, int meet, double prob, int day,int immune){
        int contacts = infected*meet;
        int newInfected = 0;
        double immuneprecent = (immune+infected)/population;

        for (int m = 1; m <= contacts; m++){
            double testnr = Math.random();
            double test = Math.round(testnr*100.0)/100.0;
            if(test <= prob){
                double testnr2 = Math.random();
                double test2 = Math.round(testnr2*100.0)/100.0;
                if(test2 >= immuneprecent){
                    newInfected++;
                }
            }
        }
        return newInfected;
    }

    
}
*/

//-----------------------

/*
VERSION 1 bacic exponential growth dosent condider immunity and herd immunity

import java.util.*;
public class virus {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("population");
        int population = sc.nextInt();
        System.out.println("people infected on day one");
        int infected = sc.nextInt();
        System.out.println("time untill one is recovered");
        int timetorec = sc.nextInt();
        System.out.println("meet how many people a day");
        int meet = sc.nextInt();
        System.out.println("infection probability 0.XX");
        double prob = sc.nextDouble();
        System.out.println("simulation time");
        int simtime = sc.nextInt();
        int day = 1;
        int[] rec;
        rec = new int[simtime];
        rec[1] = infected;
        // int immune = 0;

        while(day<=simtime){
            
            int newinfected = day(population,infected,timetorec,meet,prob,day);
            infected = infected + newinfected;

            System.out.println("day: "+day+" infeced: "+infected);
            day++;

        }

        sc.close();

        
    }

    public static int day(int population, int infected, int timetorec, int meet, double prob, int day){
        int contacts = infected*meet;
        int newInfected = 0;

        for (int m = 1; m <= contacts; m++){
            double testnr = Math.random();
            double test = Math.round(testnr*100.0)/100.0;
            if(test <= prob){
                newInfected++;
            }
        }
        return newInfected;
    }
    
}
*/


    


