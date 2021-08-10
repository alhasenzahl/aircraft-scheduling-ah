# Aircraft Scheduling App

## How to Get Project Working Locally:

1. `git clone` the project from this repo
2. run `npm install` to install any dependencies
3. run `npm run serve` to start up development server

## How I went about approaching this problem:

I read through the information provided a few times and instantly realized that there was a lot of information being provided that was all relevant, but not all of it was crucial to being able to get a very basic form of this app running.  This was especially true with an expected work window of around 3 hours.  So with that in mind, I really tried to focus on the basic points being laid out in the document.  I needed to build an app that allows the user to create a rotation for an aircraft from the list of flights and display the utilization percentage for that rotation.  Everything else, I saw as an added element that would enhance the abilities of the app and overall use of the app, but they weren't paramount for getting it running.

## Elements I would add/change to improve the app:

1. Integrate the API instead of just using the json files.
2. Put logic in place to enforce the rules for the rotation schedule of the aircrafts.
3. Add the horizontal bar for the aircraft 24 hour timeline.
4. Add and adjust elements of the app to better meet a11y standards to allow for a better user experience for all users.
5. Reconfigure some of the functions (ex: addCard()/removeCard()) that are very similar to each other from two functions into one.
6. Reconfigure some of the component templates because a couple of them ended up being very similar to each other.
7. Allow for rotations to be made for more than one day and more than one aircraft.
8. Allow the final decided rotations to be submitted to the back-end.
