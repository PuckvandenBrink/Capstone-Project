# Capstone-Project

const _ = {
clamp (number, lowerBound, upperBound) {
  let lowerClampedValue = Math.max(number, lowerBound);
  let clampedValue = Math.min(lowerClampedValue, upperBound);
  return clampedValue;
},
  inRange (number, startValue, endValue){
    if (endValue === undefined) {
     endValue = startValue
      startValue = 0     
    };
    if (startValue > endValue) {
      let temporaryValue = endValue
     endValue = startValue 
     startValue = temporaryValue
    };
  let isInRange = startValue <= number && number < endValue
     return isInRange  
  },
  words (string){
    let arrayWords = string.split(' ');
    return arrayWords;
  },
  pad (string, length){
    if (string.length >= length){
      return string
    };
    let startPaddingLength = Math.floor((length - string.length) / 2);
    let endPaddingLength = length - string.length - startPaddingLength; 
    let paddedString = ' '.repeat(startPaddingLength) + string + ' '.repeat(endPaddingLength);
    return paddedString; 
  },
  has (object, key){
    let hasValue = object[key];
    if (hasValue != undefined){
      return true;
    } else {
      return false;
    }
    return hasValue;
  },
  invert (object){
    let newObject = {};
   for (let key in object){
     let originalValue = object[key];
     newObject = {originalValue : key}
   } 
    return newObject;
  },
  findKey (object, predicateFunction){
    for (let key in object){
   let value = object[key];
      let predicateReturnValue = predicateFunction(value);
      if (predicateReturnValue){
        return key
      }
    }       
        return undefined
  },
  drop (array, numberToDrop){
    if (numberToDrop === undefined){
      numberToDrop = 1;
    }
    let copyArray = array.slice(numberToDrop); 
    return copyArray;
  },
  dropWhile (array, predicateArgument){
    const callBack = (element, index) => {
      return !predicateArgument(element, index, array);
    }
    let dropNumber = array.findIndex(callBack);
    let droppedArray = this.drop(array, dropNumber);
    return droppedArray;
  },
  chunk (array, chunkSize){
    if (chunkSize === undefined){
      chunkSize = 1;}
  let arrayChunks = [];
    for (let i = 0; i < array.length; i += chunkSize) {
      let arrayChunk = array.slice(i, i + chunkSize);
      arrayChunks.push(arrayChunk);
    }
    return arrayChunks;
  },
};


// Do not write or modify code below this line.
module.exports = _;



