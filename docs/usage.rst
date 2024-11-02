======
Example
======

.. code-block:: python

    from gpx_converter import Converter

**Just read the GPX to dictionary**

.. code-block:: python

    dic = Converter(input_file='your_input.gpx').gpx_to_dictionary(latitude_key='latitude', longitude_key='longitude')
    # Now you have a dictionary and can access the longitude and latitude values using the keys
    latitudes = dic['latitude']
    longitudes = dic['longitude']

    # Example output:
    # {
    #     "latitude": [12.34, 12.35, ...],
    #     "longitude": [45.67, 45.68, ...]
    # }

**Convert GPX to other formats**

- Convert from GPX to CSV:

.. code-block:: python

    Converter(input_file='your_input.gpx').gpx_to_csv(output_file='your_output.csv')

- Convert from GPX to Excel:

.. code-block:: python

    Converter(input_file='your_input.gpx').gpx_to_excel(output_file='your_output.xlsx')

- Convert from GPX to JSON:

.. code-block:: python

    Converter(input_file='your_input.gpx').gpx_to_json(output_file='your_output.json')

- Convert GPX file to DataFrame:

.. code-block:: python

    df = Converter(input_file='your_input.gpx').gpx_to_dataframe()
    # Example output:
    #      latitude  longitude
    # 0     12.34     45.67
    # 1     12.35     45.68
    # ...

- Convert GPX file to numpy array:

.. code-block:: python

    np_array = Converter(input_file='your_input.gpx').gpx_to_numpy_array()
    # Example output:
    # array([[12.34, 45.67],
    #        [12.35, 45.68],
    #        ...])

**Convert other formats to GPX**

- CSV to GPX

.. code-block:: python

    Converter(input_file='your_input.csv').csv_to_gpx(lats_colname='column_name_of_latitudes',
                                                      longs_colname='column_name_of_longitudes',
                                                      output_file='your_output.gpx')

    # Parameters:
    # - lats_colname: Name of the column in the CSV containing latitude values.
    # - longs_colname: Name of the column in the CSV containing longitude values.

- Excel to GPX

.. code-block:: python

    Converter(input_file='your_input.xlsx').excel_to_gpx(lats_colname='column_name_of_latitudes',
                                                         longs_colname='column_name_of_longitudes',
                                                         output_file='your_output.gpx')

- DataFrame to GPX (notice that this method is static)

.. code-block:: python

    Converter.dataframe_to_gpx(input_df=your_df,
                               lats_colname='column_name_of_latitudes',
                               longs_colname='column_name_of_longitudes',
                               output_file='your_output.gpx')

- JSON to GPX

.. code-block:: python

    Converter(input_file='your_input.json').json_to_gpx(lats_colname='column_name_of_latitudes',
                                                        longs_colname='column_name_of_longitudes',
                                                        output_file='your_output.gpx')

**Automate the conversion of multiple CSV files to GPX**

.. code-block:: python

    Converter.convert_multi_csv_to_gpx(dirpath='your_directory/')
    
    # Converts all .csv files in the specified directory to GPX format.
    # Files are outputted in the same directory.

**Apply spline interpolation on GPX file (requires scipy)**

.. code-block:: python

    interpolated_coordinates = Converter.spline_interpolation(cv=your_array_of_control_vertices)

    # Note: You need to have `scipy` installed for this function to work.

Usage from terminal
--------------------

Alternatively, you can use the `gpx_converter` directly from the terminal.
You just need to pass the function, input file, and output file as arguments.

- function: the conversion method you want to use (e.g., `gpx_to_csv`, `csv_to_gpx`)
- input file: path to your input file
- output file: path to your output file

.. code-block:: console

    $ gpx_converter --function "gpx_to_csv" --input_file "home/your_input.gpx" --output_file "home/your_output.csv"

or, you can use the short version:

.. code-block:: console

    $ gpx_converter -func "gpx_to_csv" -in "home/your_input.gpx" -out "home/your_output.csv"

Available Functions for Terminal Use
------------------------------------

- gpx_to_csv
- gpx_to_excel
- gpx_to_json
- csv_to_gpx
- excel_to_gpx
- json_to_gpx
