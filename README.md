# pickpaged

pickpacked is a wrapper around [pick](https://github.com/wong2/pick) that helps create a **paged** curses based interactive selection list in the terminal. See it in action:

![alt tag](https://raw.github.com/roubles/pickpaged/master/doc/viewlog.gif)

### Installation

    $ pip install pickpaged

### Usage

**pickpaged** comes with a simple api:

      >>> import pickpaged
      >>>
      >>> title = 'Please choose an option: '
      >>> skip = 0
      >>> limit = 2 # Two options per page
      >>> index = 0 # Which index to start cursor at
      >>> options = ['option1', 'option2', 'option3', 'option4', 'option5']
      >>> while True:
      >>>     options = getPage(skip, limit) # Your custom routine to get the options for the page
      >>>     option, index, skip = pickpaged.pickpaged(options, skip, limit, title)
      >>>     if option not in pickpaged.pager_options:
      >>>         # This is a valid option (not NEXT, PREV, REFR or EXIT)
      >>>         # Your code to work on the selected option goes here
      >>>     else:
      >>>         if option == pickpaged.EXIT:
      >>>             break

#### Options

* `options`: a list of options to choose from
* `skip`: how many options have currently been skipped
* `limit`: how many options are shown per page 
* `index`: set this to the current selected option (defaults to 0)
* `title`: (optional) a title above options list
* `indicator`: (optional) custom the selection indicator, defaults to *
* `originalSkip`: (optional) set this if the first call to pickpaged skipped some options
