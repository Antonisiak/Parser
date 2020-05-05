# Parser
package test;

import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.Iterator;

import org.json.simple.JSONArray;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.json.simple.parser.ParseException;

public class ParseJSON 
{

	public static void main(String[] args) 
	{
		JSONParser parser = new JSONParser();
		
		
		try
		{
			Object obj = parser.parse(new FileReader("test.json"));
			JSONObject jsonObject = (JSONObject) obj;
			
			Object board = jsonObject.get("number of squares");
			System.out.println("Board size : " + board);
			
			JSONArray squaresArray = (JSONArray) jsonObject.get("squares");
			Iterator<Object> iterator2 = squaresArray.iterator();
			
			while(iterator2.hasNext())
			{	
				System.out.println("Square : " + iterator2.next());
			}
			
			JSONArray playersArray = (JSONArray) jsonObject.get("players");
			Iterator<String> iterator = playersArray.iterator();
			
			while(iterator.hasNext())
			{	
				System.out.println("Player : " + iterator.next());
			}
		}
		
		catch(FileNotFoundException e) {e.printStackTrace();}
		catch(IOException e) {e.printStackTrace();}
		catch(ParseException e) {e.printStackTrace();}
		catch(Exception e) {e.printStackTrace();}

	}

}
