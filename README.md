# Crud-QueryBuilder
PHP component for more comfortable work with database, which realize crud - methods

methods:
	select
	insert
	update
	delete.		
    
    select($table, $where = [], $fields = "*", $limit=null) - must take these parameters
	   - Where:
		* $table - name of the table;
		* $where is array that contains these fields:
		  $where = array(
		      "column" => "id",
		      "comparison" => "=",
		      "value" => $id);
		* fields - enumeration of table fields;
		* limit = Number of selected objects;            
	    - Examples of using select:
	      [
		  $fields = "id, title, date, short_content";
		  $limit = [0,10];

		  $result = \Components\QueryBuilder::select("news", null, $fields, $limit);
	      ]    
	    or
	      [
		  public static function getNewsItemById($id)
		  {
		    $id = intval($id);
		    if($id){	

		      $where = array(
			"column" => "id",
			"comparison" => "=",
			"value" => $id);

			  $result = \Components\QueryBuilder::select("news", $where);
		      $newsItem = $result->fetch();
		      return $newsItem;
		    }
		  }
	      ]
      
      insert($table, $values)  - must take these parameters
	      - Where:
		* $table - name of the table;
		* $values is array that contains fields which use in table:
		    f.e.: $values = array(
			  title,
			  date("j, n, Y"),
			  short_content
			);
      
      update($table, $valuesAndColumns, $where = [])  - must take these parameters
	      - Where:
		* $table - name of the table;
		* $valuesAndColumns - key-value's array of fields which we wanna update
		  F.E. $valuesAndColumns = array(
			array('column' => 'title', 'value' => $_POST['title']),
			array('column' => 'date', 'value' => date("j, n, Y")),
			array('column' => 'short_content', 'value' => $_POST['short_content'])
		      );
		* $where is array that contains these fields:
		  $where = array(
		      "column" => "id",
		      "comparison" => "=",
		      "value" => $id);
              
	delete($table, $where) - must take these parameters
		- Where:
		  * $table - name of the table;
		  * $where is array that contains these fields:
		  $where = array(
		      "column" => "id",
		      "comparison" => "=",
		      "value" => $id);

