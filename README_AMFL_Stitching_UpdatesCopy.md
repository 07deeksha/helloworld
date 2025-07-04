# AMFL STITCHING 
### UPDATE AS OF 18 APRIL 2025

## TASK - Stitching by replacing samples filled with zeroes(due to stitching) with the nearest available previous sample 
> The raw data sometimes contains mislabeled or repeated head ids in a sample.
>> The two types of anomalous head id are: - 
>> 1. Mislabeled head id (such as instead of 1 or 2 or 3 or 4, getting some other no. say 81 in place)
>> 2. Repeated head id (such as repetition of any of the head id among 1,2,3 or 4 twice and one of them got missed)

## HANDLING 
> In the ProcessFiles() function, before calling FdConvereter(), the missing indexes based on the IEnumerable Dictionary iecd are extracted using a LINQ. Then, the filedictionary created using FdConveretr is altered for the data filled with 0s at missing frameindexes (i.e unavailable frames in raw) are filled with data of previous nearest sample. A csv named AlteredIndexes_Info0 and ErrorLoggingforAlteredIndexes is dumped stating the missing index and index used for filling that index and the other csv for logging the misslabelled head ids. Refer line 439 for the same.