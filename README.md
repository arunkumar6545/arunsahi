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
