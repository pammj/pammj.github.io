---
layout: page
title: Strains
subtitle: I Heart Jane Strains List
permalink: /strains/
---

<head>
    <title>Strain Listing</title>
    <script type="text/javascript" src="https://code.jquery.com/jquery-1.11.0.js"></script>
    <link rel="stylesheet" type="text/css" href="https://cdn.datatables.net/1.10.10/css/jquery.dataTables.min.css" />
    <script type="text/javascript" src="https://cdn.datatables.net/1.10.10/js/jquery.dataTables.min.js"></script>
    <style type="text/css">
        .filter-form {
            margin-bottom: 30px;
        }

        .filter-form div {
            margin-bottom: 10px;
        }

        .grid-container {
            display: grid;
            grid-gap: 10px;
            grid-template-columns: auto auto auto;
            padding: 10px;
        }

        .grid-item {
            background-color: rgba(255, 255, 255, 0.8);
            border: 1px solid rgba(0, 0, 0, 0.8);
            padding: 5px;
            text-align: center;
        }
    </style>
</head>

<body>
    <form class="filter-form">
        <h3>Filters</h3>
        <div class="grid-container">
            <div class="grid-item"><label>ID :</label> <input type="text" value="" class="filter"
                    data-column-index="0" /></div>
            <div class="grid-item"><label>StrainID :</label> <input type="text" value="" class="filter"
                    data-column-index="1" /></div>
            <div class="grid-item"><label>Name :</label> <input type="text" value="" class="filter"
                    data-column-index="2" /></div>
            <div class="grid-item"><label>THC :</label> <input type="text" value="" class="filter"
                    data-column-index="3" /></div>
            <div class="grid-item"><label>CBD :</label> <input type="text" value="" class="filter"
                    data-column-index="4" /></div>
            <div class="grid-item"><label>Caryophyllene :</label> <input type="text" value="" class="filter"
                    data-column-index="5" /></div>
            <div class="grid-item"><label>Humulene :</label> <input type="text" value="" class="filter"
                    data-column-index="6" /></div>
            <div class="grid-item"><label>Limonene :</label> <input type="text" value="" class="filter"
                    data-column-index="7" /></div>
            <div class="grid-item"><label>Linalool :</label> <input type="text" value="" class="filter"
                    data-column-index="8" /></div>
            <div class="grid-item"><label>Myrcene :</label> <input type="text" value="" class="filter"
                    data-column-index="9" /></div>
            <div class="grid-item"><label>Bisabolol :</label> <input type="text" value="" class="filter"
                    data-column-index="10" /></div>
            <div class="grid-item"><label>Pinene :</label> <input type="text" value="" class="filter"
                    data-column-index="11" /></div>
            <div class="grid-item"><label>Terpinolene :</label> <input type="text" value="" class="filter"
                    data-column-index="12" /></div>
            <div class="grid-item"><label>(case Weight when 1 then 'Gram' when 2 then 'Eighth' when 3 then 'Quarter'
                    when 4 then 'CONCHALFGRAM' when 5 then 'CONCGRAM' END) :</label> <input type="text" value=""
                    class="filter" data-column-index="13" /></div>
        </div>
    </form>
    <div id="example_wrapper" class="dataTables_wrapper">
        <table id="example" class="display dataTable" cellspacing="0" width="100%" role="grid"
            aria-describedby="example_info" style="width: 100%;">
            <thead>
                <tr role="row">
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> ID </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> StrainID </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Name </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> THC </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> CBD </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Caryophyllene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Humulene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Limonene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Linalool </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Myrcene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Bisabolol </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Pinene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> Terpinolene </th>
                    <th class="sorting" rowspan="1" colspan="1" style="width: 69px;"> (case Weight when 1 then 'Gram'
                        when 2 then 'Eighth' when 3 then 'Quarter' when 4 then 'CONCHALFGRAM' when 5 then 'CONCGRAM'
                        END) </th>
                </tr>
            </thead>
            <tbody id="straintbody">

            </tbody>

        </table>
    </div>
    <script type="text/javascript">
        // $("#straintbody").load("/strainbody.html");
        $(document).ready(function () {
setTimeout(function(){
    
            $.get("/strainbody.txt", function (data) {
                $('#straintbody').html(data);
                setTimeout(function(){
                    
                // DataTable
                var dtable = $("#example").DataTable();
                $(".filter").on("keyup change", function () {
                    //clear global search values
                    dtable.search("");
                    dtable.column($(this).data("columnIndex")).search(this.value).draw();
                });

                $(".dataTables_filter input").on("keyup change", function () {
                    //clear column search values
                    dtable.columns().search("");
                    //clear input values
                    $(".filter").val("");
                });
                }, 1200);

            });
}, 600);

        });


                 //]]>
    </script>
</body>