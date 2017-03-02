###### Numpy Array
- Add a column
    ```
    a = np.array([[1,2,3],[4,5,6]])
    b = np.array([[0],[0]])

    np.concatenate((a,b), axis=1)
    array([[1, 2, 3, 0],
           [4, 5, 6, 0]])
    ```


###### take command line arguments
- argparse: similar to the version in R
    ```
    import argparse
    parser = argparse.ArgumentParser(description='Predict mutation probabilities')

    parser.add_argument('-o', '--output', help='output directory', required=True)

    args = parser.parse_args()
    ```

###### Invoke system command
- subprocess

    There are many advantages of `subprocess` over `os.system`
    ```
    import subprocess as sp

    sp.call(args)
    # this can check if the command is executed correctly
    sp.check_call(args)
    # shlex.split() can be used to split arguments

    ```

    [read more on subprocess](https://docs.python.org/2/library/subprocess.html)
- os.system
    ```
    imort os
    # this will execute the command but renturn 0
    os.system(cmd)

    # to save the values returned by cmd
    output = os.popen(cmd, "r")
    while 1:
        line = p.readline()
        if not line: break
        print line
    ```


###### logging


