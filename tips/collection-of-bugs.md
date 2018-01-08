#bugs 


 * $_FILES['']
    $file_name = $_FILES[$upload_name]['name'];
    //echo "testing-".$file_name."<br>";
    //$file_name = strtolower($file_name);
    $file_extension = end(explode('.', $file_name)); //ERROR ON THIS LINE