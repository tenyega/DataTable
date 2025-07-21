DATA TABLES LEARNING 
- DataTables is a jQuery plugin that makes HTML tables interactive by adding features like:
        - Search/filter
        - Pagination
        - Sorting
        - Ajax loading
        - Export (Excel, PDF, etc.)


# Need 
  
  <!-- jQuery -->
  <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>

  <!-- DataTables CSS -->
  <link rel="stylesheet" href="https://cdn.datatables.net/1.13.6/css/jquery.dataTables.min.css">

  <!-- DataTables JS -->
  <script src="https://cdn.datatables.net/1.13.6/js/jquery.dataTables.min.js"></script>


# Activation of datatable 
    <script>
        $(document).ready(function () {
        $('#myTable').DataTable();
        });
    </script>



# Language change can be done while activation of the datatable
    <script>
    $(document).ready(function () {
        $('#example').DataTable({
        language: {
            url: "https://cdn.datatables.net/plug-ins/1.13.6/i18n/fr-FR.json"
        }
        });
    });
    </script>


# Adding Dynamic table content from a JSON file 
    <script>
    $(document).ready(function () {
        $('#ajaxTable').DataTable({  // HERE THE ajaxTable is the id of the table usergiven
        ajax: 'data.json',  // here the data.json is the name of the Json file from where i m getting the data from
        columns: [          // list of the property inside the JSON File (name, position, office, age, start_date)
            { data: 'name' },
            { data: 'position' },
            { data: 'office' },
            { data: 'age' },
            { data: 'start_date' }
        ],
        language: {   // changing the language of the datatable
            url: "https://cdn.datatables.net/plug-ins/1.13.6/i18n/fr-FR.json"
        }
        });
    });
    </script>

# Exporting to Excel, pdf, csv  We need these button extensions.  
    
        <link rel="stylesheet" href="https://cdn.datatables.net/buttons/2.4.1/css/buttons.dataTables.min.css">
        <script src="https://cdn.datatables.net/buttons/2.4.1/js/dataTables.buttons.min.js"></script>


    ##----- Depenndencies for export functions 
        <script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.10.1/jszip.min.js"></script> // this is needed to generate Excel/CSV
        <script src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.2.7/pdfmake.min.js"></script> //to generate pdf
        <script src="https://cdnjs.cloudflare.com/ajax/libs/pdfmake/0.2.7/vfs_fonts.js"></script>
        <script src="https://cdn.datatables.net/buttons/2.4.1/js/buttons.html5.min.js"></script> // enable export
        <script src="https://cdn.datatables.net/buttons/2.4.1/js/buttons.print.min.js"></script>  // and print buttons


# The table with id ajaxTable is populated dynamically using Ajax. 

# $(document).ready(function () {
  $('#ajaxTable').DataTable({
  This will wait until the HTML is fully loaded, then initialises Datatable on #ajaxTable


# data.json  should contain an array of JSON Objet and it loads it from the local file.

# Mapping JSON keys to columns of the datatable
columns: [
      { data: 'name' },
      { data: 'position' },
      { data: 'office' },
      { data: 'age' },
      { data: 'start_date' }
    ],


#     dom: 'Bfrtip',  // with out this the buttons wont print. 
    buttons: [
      'copyHtml5',
      'excelHtml5',
      'csvHtml5',
      'pdfHtml5',
      'print'
    ],
  this actually shows the button 

        dom: 'Bfrtip' tells DataTables where to place UI elements:

                B → Buttons

                f → Filter box (search)

                r → Processing display

                t → Table

                i → Info summary

                p → Pagination controls

        buttons array defines export options:

                'copyHtml5' → Copy to clipboard

                'excelHtml5' → Download as Excel

                'csvHtml5' → Download as CSV

                'pdfHtml5' → Download as PDF

                'print' → Open print view


# Modifiable Datatable. DataTables itself does not support editing by default. Can use JS or any extensions to make it editable. 

    # Client only using contenteditable as true on the event of draw on datatable.  and on submit or blur event u can call ajax function to save it at backend. 
                $('#ajaxTable').on('draw.dt', function () {
                    $('#ajaxTable tbody td').attr('contenteditable', true);
                    });
                    // draw.dt is the event of draw on datatable. draw is a built-in event provided by the DataTables jQuery plugin.
                    //The .dt suffix is a namespace that DataTables uses for its custom events. It helps avoid conflicts with other jQuery events named draw.


    # can use inline editing plusin like Datatable editor. ( paid version)

    # Use jEditable or Tabledit (Free Plugins)
            These plugins make inline editing easy:

            Tabledit — free & easy

            jEditable — classic jQuery plugin
