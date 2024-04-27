# ip-12
        
<cars>
    <car>
        <make>audi</make>
        <model>Mustang</model>
        <year>2022</year>
        <color>black</color>
     
    </car>
    <!-- Similarly for other cars -->
</cars>

<cars>
    <car>
        <make>benz</make>
        <model>Mustang</model>
        <year>2022</year>
        <color>silvery grey</color>
        <image>images/ferrari.jpg</image>
    </car>
    <!-- Similarly for other cars -->
</cars>
<cars>
    <car>
        <make>ferrari</make>
        <model>Mustang</model>
        <year>2022</year>
        <color>Red</color>
        <image>images/ferrari.jpg</image>
    </car>
    <!-- Similarly for other cars -->
</cars


</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Car Gallery</title>
    <style>
        /* CSS styling for the car gallery */
        .car {
            border: 1px solid #ccc;
            margin-bottom: 10px;
            padding: 10px;
            overflow: hidden;
            cursor: pointer;
        }
        .car img {
            max-width: 100%;
            height: auto;
        }
        #carDetails {
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="carGallery">

</div>
  
<div id="carDetails">
    <!-- Car details will be displayed here -->
</div>

<script src="https://code.jquery.com/jquery-3.7.1.min.js"></script> 
<img src="CARS/BENZIMG" alt="Image Description">
<img src="CARS/audii.img" alt="Image Description">

<img src="CARS/ferrariIMG.webpg" alt="Image Description">
<script>
$(document).ready(function() {
    // Load car data from XML file
    $.ajax({
        url: 'carss.xml',
        dataType: 'xml',
        success: function(data) {
            var carsHtml = '';
            // Loop through each car in the XML data
            $(data).find('car').each(function() {
                var make = $(this).find('make').text();
                var model = $(this).find('model').text();
                var year = $(this).find('year').text();
                var color = $(this).find('color').text();
                var image = $(this).find('image').text();

                // Create HTML for each car
                var carHtml = '<div class="car" data-make="' + make + '" data-model="' + model + '" data-year="' + year + '" data-color="' + color + '">';
                carrshtml += '<h3>' + make + ' ' + model + '</h3>';
                carrshtml += '<p>Year: ' + year + '</p>';
               carrshtml  += '<p>Color: ' + color + '</p>';
                 carrshtml  += '<img src="' + image + '" alt="' + make + ' ' + model + '">';
                carrshtml  += '</div>';

                carsHtml += carHtml;
            });
            // Display the car gallery
            $('#carGallery').html(carrs.html);
        },
        error: function(xhr, status, error) {
            console.error("AJAX Error:", status, error);
            $('#carGallery').html('<p>Error loading car data.</p>');
        }
    });

    // Display car details when an image is clicked
    $(document).on('click', '.car img', function() {
        var $car = $(this).closest('.car');
        var make = $car.data('make');
        var model = $car.data('model');
        var year = $car.data('year');
        var color = $car.data('color');
        
        var detailsHtml = '<h3>' + make + ' ' + model + '</h3>';
        detailsHtml += '<p>Year: ' + year + '</p>';
        detailsHtml += '<p>Color: ' + color + '</p>';
        
        $('#carDetails').html(detailsHtml);
    });
});
</script>

</body>
</html>

