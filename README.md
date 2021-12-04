# Java-COBIS-Convenience-

package com.company;
import java.util.ArrayList;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        ArrayList<String> product = new ArrayList<String>();
        ArrayList<Double> prices = new ArrayList<Double>();
        ArrayList<String> customerOrder = new ArrayList<String>();
        ArrayList<Integer> productQuantity = new ArrayList<Integer>();

        product.add("Red-Hot Spicy Doritos");
        prices.add(2.99);
        product.add("Cool Ranch Doritos");
        prices.add(2.99);
        product.add("Coke");
        prices.add(0.99);
        product.add("Diet Coke");
        prices.add(0.99);
        product.add("Pepsi");
        prices.add(0.99);
        product.add("Five Hour Energy");
        prices.add(3.99);
        product.add("Sunflower Seeds");
        prices.add(0.99);
        product.add("Peanuts");
        prices.add(0.99);
        product.add("Mac Book Chargers");
        prices.add(120.00);
        product.add("Dell Chargers");
        prices.add(50.00);

        System.out.println("Welcome to COBIS Convenience Store!\n");
        System.out.println("The ten items offered are displayed below: ");
        System.out.println("0 :  Red-Hot Spicy Doritos" +
                "\n1 :  Cool ranch Doritos" +
                "\n2 :  Coke" +
                "\n3 :  Diet Coke" +
                "\n4 :  Pepsi" +
                "\n5 :  Five Hour Energy" +
                "\n6 :  Sunflower seeds" +
                "\n7 :  Peanuts" +
                "\n8 :  Mac Book Chargers" +
                "\n9 : Dell Chargers");

        Scanner response = new Scanner(System.in);
        String customerInput;
        StringBuilder output = new StringBuilder();
        double orderTotal;
        double grandTotal = 0;


        System.out.println("Enter your name or type done if finished");
        while(!(customerInput = response.nextLine()).equalsIgnoreCase("done")) {
            output.append(customerInput);
            orderTotal = 0;
            do {
                System.out.println("Enter the item number of the product you would like to buy type 10 when finished. ");

                customerInput = response.nextLine();
                for(String prod :product) {
                    if(Integer.parseInt(customerInput)==(product.indexOf(prod) )) {
                        product.get(product.indexOf(prod));
                        orderTotal += prices.get(product.indexOf(prod));
                        String itemname = product.get(Integer.parseInt(customerInput));
                        output.append("\n").append(itemname);
                        if(!customerOrder.contains(customerInput)) {
                            customerOrder.add(customerInput);
                            productQuantity.add(1);
                        }
                        else {
                            int indexnum = customerOrder.indexOf(customerInput);
                            productQuantity.set(indexnum, productQuantity.get(indexnum) + 1);
                        }
                        break;
                    }
                }
            }while ((!customerInput.equalsIgnoreCase("10")));
            output.append(" \n \t\t\t").append(orderTotal).append("\n");
            grandTotal += orderTotal;

            System.out.println("Enter the name of the next customer or if the store is closed type done. ");
        }
        System.out.println( "The COBIS Convenience Store is now Closed. ");

        System.out.println("\n" + "Closing Receipts  \n  "  + output);

        System.out.println("Inventory Sold ");
        System.out.println(" ");

        for(String inventoryquantity :customerOrder) {

            System.out.println(  "Item Number " + inventoryquantity + ":" + " [" + productQuantity.get(customerOrder.indexOf(inventoryquantity))+"]");
        }

        System.out.println(" ");
        System.out.println("Grand Total: $"  + grandTotal);

    }
}
