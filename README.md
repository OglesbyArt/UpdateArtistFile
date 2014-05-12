UpdateArtistFile
================
public class UpdateArtistFile  
{

    //Desc: updates the Artist file by searching for the last name of the artist
    //Pre: the ArtistFile.txt file must exist
    //Post: The Artist file is updated
    public static void updateArtistFile()
    {

    try
    {
	boolean	      done = false;		        // terminates while-loop
	boolean	      found = false;		        // tells if investment is found
	char	      c;			        // character entered by user
	String        fName;                            // buffer for line of characters
        String        lName;
	char	      choice;	                        // user's choice
        Artist    a = new Artist();    // investment to be modified

	while (!found && !done)
	{
            System.out.println ("Please enter the first name and press <ENTER> and last name of Artist and press <ENTER>" +
                                " you want to change : ");

            fName = UserInterface.getString();
            lName = UserInterface.getString();

	    found = a.find (fName,lName);

	    if (!found)
	    {
		System.out.println ("Artist " + fName +" "+ lName + " was not found.");
		System.out.println ("Would you like to enter another Artist Name?");

		choice = UserInterface.getChar();

		if (choice == 'n')
		{
		  done = true;
		}
            }
	}

	if (!found)
	{
	    return;
	}

	while (!done)
	{
		while (!done)
		{
                    UserInterface.clearScreen ();

                    System.out.println ("\t           UPDATE ARTIST\n\n");
                    System.out.println ("\t Oglesby Art Pricing System\n\n");
                    System.out.println ("\t        1. Update Artist first name\n");
                    System.out.println ("\t        2. Update Artist last name\n");
                    System.out.println ("\t        3. Update Artist fashionability value\n");
                    System.out.println ("\t        4. Exit to menu\n\n");
                    System.out.println ("Enter your choice and press <ENTER>: ");

                    try
                    {
			choice = UserInterface.getChar();

			switch (choice)
			{
                            case '1':
                                a.updateArtistsFirstName();
                                break;

                            case '2':
                                a.updateArtistLastName();
                                break;
                            
                            case '3':
                              a.updateFashionabilityValue();
                              break;

                            case '4':
                            case '\n':
                              done = true;
				  break;

                            default:
                              System.out.println ("\n\nNot a valid choice\n");
                              UserInterface.pressEnter();
                              break;
			}
                     }
			catch (Exception e)
			{
			    System.out.println ("***** Error: UpdateArtistFile.updateArtist() *****");
			    System.out.println ("\t" + e);
			}

			if (!done)
			{
		            a.print ();
		            UserInterface.pressEnter();
			}
                }
        }

	a.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: AssetManager.manageInvestment() () *****");
	    System.out.println ("\t" + e);
    }

  }  
	

    //Desc: adds a new artist file to the text file
    //Pre: the ArtistFile.txt file must exist
    //Post: A new artist file is created
    public static void addArtistFile()	
    {
        try
        {
            boolean	      done = false;		        // terminates while-loop
            char	      choice;	                        // user's choice
            Artist    a = new Artist();    // investment to be modified

		while (!done)
		{
			UserInterface.clearScreen ();

			System.out.println ("\t           ADD NEW ARTIST TO FILE\n\n");
			System.out.println ("\t Oglesby Art Pricing System\n\n");
			System.out.println ("\t        Enter 'q' and press <ENTER> to return to menu\n\n\n");
                        System.out.println ("\t        Enter Artists First Name: ");
                        String fname = UserInterface.getString();
                        a.setArtistFirstName(fname);
			System.out.println ("\t        Enter Artists Last Name: ");
                        String lname = UserInterface.getString();
                        a.setArtistLastName(lname);
			System.out.println ("\t        Enter Artists Fashionability Value: ");
                        int fash = UserInterface.getInt();
                        a.setArtistFashionabilityValue(fash);

			try
			{
			    choice = UserInterface.getChar();
                            if (choice =='q')
                            {
				break;
                            }
			}
			 
			catch (Exception e)
			{
			    System.out.println ("***** Error: UpdateArtistFile.updateArtist() *****");
			    System.out.println ("\t" + e);
			}

			if (!done)
			{
		            a.print ();
		            UserInterface.pressEnter();
			}
		    }
		

	a.save ();
    }
    catch (Exception e)
    {
	    System.out.println ("***** Error: AssetManager.manageInvestment() () *****");
	    System.out.println ("\t" + e);
    }

  }  

	//Desc: deletes the artist file selected by searching for lastname, 
    //      firstname
    //Pre: the ArtistFile.txt file must exist
    //Post: The Artist file is deleted
    public static void deleteArtistFile()
    {
        Artist a = new Artist();
	a.delete();
    }
}
