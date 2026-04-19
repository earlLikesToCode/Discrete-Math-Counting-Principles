import java.util.Scanner;

public class principles{

    static Scanner input = new Scanner(System.in);
    public static void main(String[] args){


            //Main Menu

            while(true){

                //Outputs Menu
                
                switch (Menu()) {
                    case 1:
                        ruleAddition();
                        break;
                    case 2:
                        ruleProduct();
                        break;
                    case 3:
                        permutation();
                        break;
                    case 4:
                        combinations();
                        break;
                    case 5:
                        if(exit()){
                            return;
                        }else{
                            System.out.println("Cancelled");
                            System.out.println("");
                        }
                        break;
                    default: //If user picks numbers more than 5
                        System.out.println("Invalid Option!, Pick Again");
                        System.out.println("");
                        break;
                }
            }
    }

    //Menu Display

    public static int Menu(){
        
        System.out.println("----[Menu]----");
        System.out.println("[1] Rule of Addition");
        System.out.println("[2] Rule of Product");
        System.out.println("[3] Permutations {ORDER MATTERS}");
        System.out.println("[4] Combinations {ORDER DOES NOT MATTER}");
        System.out.println("[5] Exit");
        System.out.println("");
        System.out.print("Enter Choice: ");
        
        int choice = input.nextInt();
        input.nextLine();

        return choice;

    }

    //Addition

    public static void ruleAddition(){
        int total =  0;
        int Num[] = new int[50];
        int count = 0;
        int count2 = 0;
        int numCategory = 0;
        
        //Category

        do{ //Prevents user from picking 0, Catergory = Type of Choices [foods (Catergory), Cookies & Bread ( 2 Choices)]
        System.out.print("Enter Number of the Category of Choices: ");
        numCategory = input.nextInt(); //For category

        if(numCategory <= 0){
            System.out.println("Invalid Input!, Try Again");
            System.out.println("");
        }
        }while(numCategory <= 0);
        

        //Choices


        for(int i = 1; i <= numCategory;i++){
            System.out.print("Enter Amount of Choice for Category #" + i + ": ");
            Num[count]= input.nextInt();
            total += Num[count];
            count++;
        }


        // Dispaly Total Available Choices

         System.out.println(" ");
         System.out.print("Total Choices Available: " + total + " = ");
         System.out.println(" ");

        // Display Solution for computing Total Choices

        for(int k = 1; k <= numCategory; k++){
            System.out.print("Choice No." + k + " > " + "Choices: "+ Num[count2] + " + "  );
            System.out.println("");
            count2++;
        }
        System.out.println("");



    }

    //Product

    public static void ruleProduct(){

        int numCategory = 0;
        int num[] = new int[50];
        int count = 0;
        int count2 = 0;
        int total = 1;

        //Catergory

        do{ //Same execution with addtion
        System.out.print("Enter Number of the Category of Choices: ");
        numCategory = input.nextInt();

        if(numCategory <= 0){
            System.out.println("Invalid Input!, Try Again");
            System.out.println("");
        }
        }while(numCategory <= 0);

        //Choices

        for(int i = 1; i <= numCategory; i++){
            System.out.print("Enter Amount of Choice for Category#" + i + ": " );
            num[count] = input.nextInt();
            total *= num[count];
            count++;
        }

        //Display total Available Choices

         System.out.println(" ");
         System.out.print("Total Choices Available: " + total + " = ");
         System.out.println(" ");

        //Display Solution for computing total Choices

         for(int k = 1; k <= numCategory; k++){
            System.out.print("Choice No." + k + " > " + "Choices: "+ num[count2] + " x "  );
            System.out.println("");
            count2++;
        }
        System.out.println("");


    }

        //Permutation

    public static void permutation(){
        
        
        //PERMUTAION - USED WHEN ORDER MATTER
        
        
        int choices = 0;
        int slots = 0;

        int totalChoices = 1;
        int totalSlots = 1;

        int total = 0;
        
        //FORMULA 

        System.out.println("FORMULA > NPR = N!/(N-R)! ");
        System.out.println("");

        
        //Objects (N in NPR)

        do {//Same Execution in addition and Product
        System.out.print("Enter the Amount Of Objects(N): ");
        choices = input.nextInt();

        if(choices <= 0){
            System.out.println("Error Input!, Try Again");
            System.out.println("");
        }
         }while (choices <= 0); 
        

        //Selection (R in NPR)

        do{
        System.out.print("Enter Amount of Selections for Objects(R): ");
        slots = input.nextInt();

        if(slots <= 0){
            System.out.println("Error Input!, Try Again");
            System.out.println("");
        }else if(slots > choices){
            System.out.println("Selections should not be more that Objects!, Try Again");
            System.out.println("");
        }
        }while (slots <= 0 || slots > choices);

        //Calculates N!

        for(int i = 1; i <= choices; i++){
            totalChoices *= i;
        }

        int newslots = 0;

        newslots = choices - slots; //Calculates (N - R)! in N!/(N-R)!

        //Calculates R!

        for(int i = 1; i <= newslots; i++){
            totalSlots *= i;    
        }
        total = totalChoices / totalSlots;

        //Display Results and Solution

        System.out.println("Total Ways when Order Matters: " + total);
        System.out.println("");
        System.out.print("N! = ");
        for(int i = 1; i <= choices; i++){
            System.out.print(i);

            if(i >=  choices){
                break;
            }

            System.out.print(" x ");
        
        }

        System.out.println("");
        System.out.print("R! = ");

        for(int i = 1; i <= slots; i++){
            System.out.print(i);

            if(i >=  slots){
                break;
            }

            System.out.print(" x ");
        
        }
        System.out.println("");
        System.out.println("");
        System.out.println(choices + "!" + " / " + "(" + choices + " - " + slots + ")" + "!");
        System.out.println(choices + "!" + " / " + newslots +"!");
        System.out.println(totalChoices + " / " + totalSlots );
        System.out.println("");
    }

    //Combinations

    static void combinations(){
        
        //Combination - USED WHEN ORDER DOES NOT MATTER
        
        int choices = 0;
        int slots = 0;

        int totalChoices = 1;
        int totalSlots = 1;

        int total = 0;

        //Formula                                                      
        System.out.println("FORMULA > NCR = (N!)/(N - R)! R!");     
        System.out.println("");                                     

        //Objects N in NCR

        do {
        System.out.print("Enter the Amount Of Objects(N): ");
        choices = input.nextInt();

        if(choices <= 0){                                                   
            System.out.println("Error Input!, Try Again");
            System.out.println(""); 
        }
         }while (choices <= 0); 
        
         //Selections R in NCR

        do{
        System.out.print("Enter Amount of Selections for Objects(R): ");
        slots = input.nextInt();
        
        if(slots <= 0){
            System.out.println("Error Input!, Try Again");
            System.out.println("");
        }else if(slots > choices){
            System.out.println("Selections should not be more than Objects!, Try Again");
            System.out.println("");
        }
        }while (slots <= 0 || slots > choices);

        //Calculates N!

        for(int i = 1; i <= choices; i++){
            totalChoices *= i;
        }

        int newslots = 0;
        int secondSlots = 0;
        int totalSecondSlots = 1;
        int totalAllSlots = 1;

        newslots = choices - slots; //Calculates (N - R)! in N!/(N-R)!
        secondSlots = slots;
        

        //Calculates R! in (N - R) R! <-- 

        for(int i = 1; i <= newslots; i++){
            totalSlots *= i;
        }


        for (int i = 1; i <= secondSlots; i ++){
            totalSecondSlots *= i;
        }

        //Calculates   N! /R! R! 

        totalAllSlots = totalSlots * totalSecondSlots; 
        total = totalChoices / totalAllSlots;
        
        //Display Results and Solutions

        System.out.println("Total Ways when Order Does NOT Matters: " + total);
        System.out.print("N! = ");

        for(int i = 1; i <= choices; i++){
            System.out.print(i);

            if(i >=  choices){
                break;
            }

            System.out.print(" x ");
        
        }

        System.out.println("");
        System.out.print("R! = ");

        for(int i = 1; i <= slots; i++){
            System.out.print(i);

            if(i >=  slots){
                break;
            }

            System.out.print(" x ");
        
        }
        System.out.println("");
        System.out.println("");
        System.out.println(choices + "!" + " / " + "(" + choices + " - " + slots + ")" + "! " + slots + "!");
        System.out.println(choices + "!" + " / " + newslots + "! " + slots + "!");
        System.out.println(totalChoices + " / " + totalAllSlots);
        System.out.println("");
    }

    //Exit with Confirmation

    static boolean exit(){
        boolean  yesNo;
        while(true){
        System.out.print("Are you sure?(Yes/No): ");
        String confirm = input.nextLine().trim().toLowerCase();
        
        switch (confirm) {
            case "yes":
                yesNo = true;
                break;
            case "no":
                yesNo = false;
                break;
            default:
                System.out.println("Invalid Option, Try Again");
                System.out.println("");
                continue;
            }
            break;
        }

        return yesNo;
    }
}
