# Readings
* [AutoComplete](https://itnext.io/using-angular-6-material-auto-complete-with-async-data-6d89501c4b79)
* [Clone Object](https://medium.com/better-programming/3-ways-to-clone-objects-in-javascript-f752d148054d)
* [Loading Indicator](https://medium.com/angular-in-depth/angular-show-loading-indicator-when-obs-async-is-not-yet-resolved-9d8e5497dd8)
* https://medium.com/@wojtrawi
* [Sharing Data](https://www.intersysconsulting.com/blog/angular-components/)

# Template
{{data | json}}

# valueChanges
```
this.rform
   .controls["inputOne"]
   .valueChanges
   .subscribe(selectedValue => {
        console.log('New Value: ', selectedValue);       // New value
        console.log('Old Value: ', this.rform.value['inputOne']); // old value
   });
```   
Ref: https://stackoverflow.com/questions/58860222/angular-reactive-form-having-the-old-value-on-change-event-callback
