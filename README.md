# ShapeFile
by @author Juan Carlos Gonzalez Ulloa  jgonzalez@innox.com.mx  &amp; Edited by David Granqvist


/**
	* This class is under GPL Licencense Agreement
	* @author Juan Carlos Gonzalez Ulloa <jgonzalez@innox.com.mx>
	* Innovacion Inteligente S de RL de CV (Innox)
	* Lopez Mateos Sur 2077 - Z16
	* Col. Jardines de Plaza del Sol
	* Guadalajara, Jalisco
	* CP 44510
	* Mexico
	*
	* Class to read SHP files and modify the DBF related information
	* Just create the object and all the records will be saved in $shp->records
	* Each record has the "shp_data" and "dbf_data" arrays with the record information
	* You can modify the DBF information using the $shp_record->setDBFInformation($data)
	* The $data must be an array with the DBF's row data.
	*
	* Performance issues:
* Because the class opens and fetches all the information (records/dbf info)
	* from the file, the loading time and memory amount neede may be way to much.
	* Example:
*   15 seconds loading a 210907 points shape file
	*   60Mb memory limit needed
	*   Athlon XP 2200+
	*   Mandrake 10 OS
	*
	*
	*
	* Edited by David Granqvist March 2008 for better performance on large files
	* This version only get the information it really needs
	* Get one record at a time to save memory, means that you can work with very large files.
	* Does not load the information until you tell it too (saves time)
	* Added an option to not read the polygon points can be handy sometimes, and saves time :-)
	* 
	* Example:
		
	//sets the options to show the polygon points, 'noparts' => true would skip that and save time
	$options = array('noparts' => false);
	$shp = new ShapeFile("../../php/shapefile/file.shp",$options); 

	//Dump the ten first records
	$i = 0;
	while ($record = $shp->getNext() and $i<10) {
		$dbf_data = $record->getDbfData();
		$shp_data = $record->getShpData();
		//Dump the information
		var_dump($dbf_data);
		var_dump($shp_data);
		$i++;
	}
	* 
	*/


