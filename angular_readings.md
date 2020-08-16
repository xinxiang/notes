# pipe
## highlight
```
@Pipe({ name: 'highlight' })
export class HighlightPipe implements PipeTransform {
  transform(text: string, search): string {
    const pattern = search
      .replace(/[\-\[\]\/\{\}\(\)\*\+\?\.\\\^\$\|]/g, "\\$&")
      .split(' ')
      .filter(t => t.length > 0)
      .join('|');
    const regex = new RegExp(pattern, 'gi');

    return search ? text.replace(regex, match => `<b>${match}</b>`) : text;
  }
}
```
* https://stackoverflow.com/questions/49653410/mat-autocomplete-filter-to-hightlight-partial-string-matches

```
<form class="example-form">
	<mat-form-field class="example-full-width">
		<input matInput placeholder="State" aria-label="State" [matAutocomplete]="auto" [formControl]="stateCtrl">
		<mat-autocomplete #auto="matAutocomplete">
			<mat-option *ngFor="let state of filteredStates | async" [value]="state.name">
        <span [innerHTML]="state.name | highLight: toHighlight : stateCtrl.value"></span>
				<span></span>
			</mat-option>
		</mat-autocomplete>
	</mat-form-field>
</form>
<button mat-button (click)="reset()" >reset</button>
```

* https://stackblitz.com/edit/angular-nue8pb-13no5c?file=app%2Fautocomplete-overview-example.html

# Readings
* [AutoComplete](https://itnext.io/using-angular-6-material-auto-complete-with-async-data-6d89501c4b79)
* [Clone Object](https://medium.com/better-programming/3-ways-to-clone-objects-in-javascript-f752d148054d)
* [Loading Indicator](https://medium.com/angular-in-depth/angular-show-loading-indicator-when-obs-async-is-not-yet-resolved-9d8e5497dd8)
* https://medium.com/@wojtrawi
* [Sharing Data](https://www.intersysconsulting.com/blog/angular-components/)
* Handle Errors:
  * [Interceptors](https://www.digitalocean.com/community/tutorials/how-to-use-angular-interceptors-to-manage-http-requests-and-error-handling)

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
