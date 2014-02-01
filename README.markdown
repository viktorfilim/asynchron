Very small library that add the wait, async pattern to promises in Java Script (currently we are using Q library).
It is just syntactic sugar on promises's APIs but I'm a complexity hater and this can clean your code.

## Example 1: reading the content of a file

        var myFileContent = fs.readFile.async("fileName.txt");
        (function(content){
            console.log(content);
        }).wait(myfilecontent);

        //myFileContent is a Q promise and you can do other things with this promise

## Example 2:

> For example, we have 2 functions (asynchronous APIs for dealing with penguins), using node.js return convention


        loadPenguin(nickName, callBack)
        loadPenguinFamily(father, mother, callBack)

> now, let's see how we load some Penguins

        var father = loadPenguin.async('MrPenguin');
        var mother = loadPenguin.async('MrsPenguin');
        var family = loadPenguinFamily.async(father, mother);

        (function (family){
            console.log(family); //whatever
        }).wait(family);

##  Simple API:

### wait(<list of variables>)

    functionReference.wait(...)

>   calls the function when all promises are fulfilled

### async(<list of variables>)

    functionReference.async(...)

> creates a promise that get fulfilled when all the arguments are ready

### nasync(<list of variables>)

> similar with async but ignores errors, fulfills the promise with a null value...
> the programmer is testing for null himself, in many cases errors are normal and part of the logic (missing a key in cache, etc)


### fail(<list of variables>)

    functionReference.fail(...)

> call the function when a promise given as argument has failed

### timeout(timeout, <list of variables>)

    functionReference.fail(...)

> like fail, but also get called if any promise given as arguments is unfulfilled until timeout expires