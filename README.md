# hemaprabhu-zoho-mini-application
ZOHO mini app
import java.util.*;

class ATM {
    private static Scanner sc;
    static int s = 10000;
    static int am[] = { 0, 0, 0, 0 };
    static int ama[] = { 0, 0, 0, 0 };
    static int mm ;
    static int bal = 0;
    static int uspa = 973739;
    static int oo = 0;
    static int so = 0;
    static int ao = 0;
    static int eo = 0;
    static int depo;

    static void startatm() {
        Scanner sc = new Scanner(System.in);
        System.out.println("ATM MACHINES");
        System.out.println("1.Admin login");
        System.out.println("2.User login");
        System.out.println("3.Exit");
        System.out.println("Enter the your login");
        int e = sc.nextInt();
        if (e == 1) {
            adminlogin();
        } else if (e == 2) {
            userlogin();
        } else if (e == 3) {
            exit();
        } else {
            System.out.println("Invalid Input");
            startatm();
        }
    }

    static void adminlogin() {
        sc = new Scanner(System.in);
        System.out.print("1.Enter Username:");
        String al = sc.nextLine();
        System.out.print("2.Enter Password:");
        String pa = sc.nextLine();
        if (al.equals("admin") && pa.equals("345678")) {
            adlogin();
        } else {
            System.out.println("wrong admin");
            startatm();
        }
    }

    static void adlogin() {
        sc = new Scanner(System.in);
        System.out.println("1.Load Amount");
        System.out.println("2.Balance");
        System.out.println("3.Back");
        int adl = sc.nextInt();
        switch (adl) {
            case 1:
                loadamount();
                break;
            case 2:
                balancead();
                break;
            case 3:
                back();
                break;
        }
    }

    static void loadamount() {
        System.out.println("no.of.2000 notes:");
        am[0] += sc.nextInt();
        System.out.println("no.of.500 notes:");
        am[1] += sc.nextInt();
        System.out.println("no.of.200 notes:");
        am[2] += sc.nextInt();
        System.out.println("no.of.100 notes:");
        am[3] += sc.nextInt();
        adlogin();


    }

    static void balancead() {
        int oo = (am[0] * 2000);
        System.out.println("amount of 2000's : " + oo + " " + am[0]);
        int so = (am[1] * 500);
        System.out.println("amount of 500's : " + so + " " + am[1]);
        int ao = (am[2] * 200);
        System.out.println("amountof 200's : " + ao + " " + am[2]);
        int eo = (am[3] * 100);
        System.out.println("amount of 100's : " + eo + " " + am[3]);
        int mm = ((oo + so + ao + eo)-bal)+depo;
        System.out.println("total : " + mm);
        if(am[0]>ama[0]){
            am[0]-=ama[0];
            System.out.println("amount of 2000's : " + oo + " " + am[0]);
        }
        if(am[1]>ama[1]){
            am[1]-=ama[1];
            System.out.println("amount of 500's : " + so + " " + am[1]);
        }
        if(am[2]>ama[2]){
            am[2]-=ama[2];
            System.out.println("amountof 200's : " + ao + " " + am[2]);
        }
        if(am[3]>ama[3]){
            am[3]-=ama[3];
            System.out.println("amount of 100's : " + eo + " " + am[3]);
        }
        int a = sc.nextInt();
        if (a == 0) {
            startatm();
        }
    }

    static void back() {
        startatm();
    }

    static void userlogin() {
        sc = new Scanner(System.in);
        System.out.println("1.Enter Username");
        String a = sc.nextLine();
        System.out.println("2.Enter User password");
        int b = sc.nextInt();
        if (a.equals("hema") && b==uspa) {
            uslogin();
        } else {
            System.out.println("wrong user");
            startatm();
        }
    }

    static void uslogin() {
        sc = new Scanner(System.in);
        System.out.println("1.Withdraw");
        System.out.println("2.View balance");
        System.out.println("3.pin change");
        System.out.println("4.Deposite");
        int wd = sc.nextInt();
        switch (wd) {
            case 1:
                withdraw();
                break;
            case 2:
                viewbalance();
                break;
            case 3:
                pinchange();
                break;
            case 4:
                deposite();
                break;
        }
    }

    static void withdraw() {
        sc = new Scanner(System.in);
        System.out.print("Enter Amount:");
        int Amount = sc.nextInt();
        for (int i = 0; i < 4; i++) {
            if (Amount % am[i] == 0) {
                s = s - Amount;
                bal = Amount;
                trans(Amount);
                System.out.println("Amount withdraw successfully");
                for(int j=0;j<4;j++){
                    System.out.println(ama[j]);
                }
                int maa = sc.nextInt();
                if (maa == 0) {
                    startatm();
                }
            } else {
                System.out.println("Invalid");
                int ha = sc.nextInt();
            }
        }
    }

    static void trans(int n) {
        if(n/2000!=0){
            ama[0]=n/2000;
            n=n%2000;
        }
        if(n/500!=0){
            ama[1]=n/500;
            n=n%500;
        }
        if(n/200!=0){
            ama[2]=n/200;
            n=n%200;
        }
        if(n/100!=0){
            ama[3]=n/100;
            n=n%100;
        }
    }

    static void viewbalance() {
        if (s >= 0) {
            System.out.println("balance:" + s);
        } else{

        }
        int maa = sc.nextInt();
                if (maa == 0) {
                    startatm();
                }

    }

    static void pinchange() {
        sc = new Scanner(System.in);
        System.out.print("Old password : ");
        int a6 = sc.nextInt();
        if (uspa == a6) {
            System.out.print("New password: ");
            int a7=sc.nextInt();
            System.out.print("Enter the password again :");
            int a8=sc.nextInt();
            if(a7==a8){
                uspa=a8;
                System.out.println("Pin changed successfully");
            }else{
                System.out.println("doesn't match");
            }
        }else{
            System.out.println("Password error");
                }
                int b1=sc.nextInt();
                if(b1==0){
                    startatm();
                }
    }

    static void deposite() {
        int depo=sc.nextInt();
        int y=s+depo;
        System.out.println(y);
        System.out.println(mm);
        int maa = sc.nextInt();
                if (maa == 0) {
                    uslogin();
                }
    }

    static void exit() {
        startatm();
    }

    public static void main(String[] arg) {
        sc = new Scanner(System.in);
        startatm();

    }
}
