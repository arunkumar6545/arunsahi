Using Angular 6 Material Auto-complete With Async Data
Fetching the options from the server

this.usersForm = this.fb.group({
  userInput: null
})

this.filteredUsers = this.usersForm
  .get('userInput')
  .valueChanges
  .pipe(
    debounceTime(300),
    switchMap(value => this.appService.search({name: value}, 1))
   );


<mat-autocomplete #auto="matAutocomplete" [displayWith]="displayFn">
  <mat-option *ngFor="let user of (filteredUsers | async)?.results" [value]="user">
    <span>{{ user.name }}</span>
    <small> | ID: {{user.id}}</small>
  </mat-option>
</mat-autocomplete>
