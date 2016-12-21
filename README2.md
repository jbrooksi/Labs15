
package com.gr.lab15;

import java.io.BufferedReader;
import java.io.BufferedWriter;
import java.io.File;
import java.io.FileReader;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.util.ArrayList;

public class CountriesTextFile {


	public static void writeToCountriesList(String filename, String countryName) {
		Path filePath = Paths.get(filename);
		// if file does not exist then create it
		if (Files.notExists(filePath)) {
			System.out.println("File does not exist, creating...");
			// create it
			try {
				Files.createFile(filePath);
				filePath = Paths.get(filename);
			} catch (IOException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
		// Now append country name to file
		//File file = filePath.toFile();
		try (PrintWriter out = new PrintWriter(new BufferedWriter(new FileWriter(filename,false)))) {
			out.println(countryName);//overwrites data in file
//			out.append(countryName);
		} catch (IOException e) {
			e.printStackTrace();
		}
	}

	
	public static ArrayList<String> readListOfCountries(String fileName) {
		ArrayList<String> returnList = new ArrayList<String>();
		
		// if file does not exist return null
		Path filePath = Paths.get(fileName);
		if (Files.notExists(filePath)) {
			return null;
		}
		try (BufferedReader in = new BufferedReader(new FileReader(fileName))) {
			while(in.ready()){
				String line = in.readLine();				
				returnList.add(line);	
			}				
		} catch (IOException e) {
			e.printStackTrace();
		}
		return returnList;
	}

}
