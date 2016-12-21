# Labs15
**
 * 
 */
package com.gr.lab15;

import java.util.ArrayList;
import java.util.Scanner;


public class CountriesApp {

	
	public static void main(String[] args) {
		Scanner scan = new Scanner(System.in);
		String fileName = "countryList.txt";
		ArrayList<String> countryList =  new ArrayList<String>();
		// This class contains the user interface (UI) for displaying
		// menus
		System.out.println("Welcome to the Countries Maintenance Application");
		boolean running = true;
		while (running) {
			System.out.println("1-See the list of countries\n2-Add a country\n3-Exit");
			System.out.print("Enter menu number:");			
			
			int choice = scan.nextInt();
			System.out.println();//newline
//			scan.next();//consume
			switch (choice) {
			case 1:// list countries
				countryList = CountriesTextFile.readListOfCountries(fileName);
				if(countryList == null){
					System.out.println("List is empty. Select option 1 first to add items to the list.\n");
				}else{
					displayOutput(countryList);
				}			
				break;

			case 2:// Add a country
				System.out.print("Enter country name:");							
				String countryName = scan.next();
				System.out.println();//newline
				CountriesTextFile.writeToCountriesList(fileName, countryName);
				break;

			case 3:// exit
				running = false;
				break;

			default:
				// null for now
				break;
			}
		}
		System.out.println("Thank you for using Countries Maintenance Application!");
	}

	private static void displayOutput(ArrayList<String> countryList) {
		System.out.println("---------Countries---------");
		for(String value: countryList){
			System.out.println(value);
		}
		System.out.println();
	}
}
