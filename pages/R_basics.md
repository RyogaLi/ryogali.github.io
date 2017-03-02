###### Data Frame
- convert every element in a col in dataframe to another type
    ```
    transform(d, col=as.numeric(col))
    ```


###### Parse command line arguments
- argparse
    ```
    library("argparse")
    parser <- ArgumentParser()
    parser$add_argument("-i", "--input", help="input file name")
    parser$add_argument(file, nargs=1, help="file to be processed")

    args <- parser$parse_args()
    input <- args$input
    file <- args$file
    ```


###### Invoke system command
   - system



   - pipe

