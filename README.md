# Gig On A Map - Project 2 - Reactathon #
Pair Project
<br />
Duration: 2 days


# Task #
Using ReactJs, build a Frontend web app that uses a 3rd party API of our choice. We had the option to use more than one


# Our Idea #
Build a web app that allowed users to find gigs in their vicinity as opposed to having to do a search.
<br />
For the design, we wanted to try and have all the events show on a map as opposed to a listed index page.
<br />
<br />
The APIs we used were:
- *SkiddleAPI* for the gig data
- *MapBoxGL* to display the events on an interactive map

Built With:
- Reactjs
- Express
- Node.js
- SCSS/CSS

#  The Project #

Deployed and can be found at: gigonamap.herokuapp.com

<a href="https://imgur.com/xURnFuT"><img src="https://i.imgur.com/xURnFuT.png" title="source: imgur.com" /></a>

```return (
      <>
        <div className={`container ${this.state.active ? 'container transition' : '' }`}>
          <p className={numberOfGigs}>{`There are ${this.props.results.length} gigs in your area`}</p>
          <div className={classes}>

            <h3>{this.state.eventData.eventname}</h3>
            <p>{this.state.eventData.description}</p>
            <img className='imgShow' src={this.state.eventData.imageurl}></img>
            
            <p>{`Tickets are ${this.state.eventData.entryprice}`}</p>
            {/* <p>{`Date ${this.state.eventData.date}`}</p> */}
            
            <p>{`Doors: ${this.state.openingtimes.doorsopen} - ${this.state.openingtimes.doorsclose}`}</p>
            <p>{`Last entry is ${this.state.openingtimes.lastentry}`}</p>
            <a target="blank" href={this.state.eventData.link}>Purchase your ticket Here</a>
          </div>
        </div>

        <ReactMapGL {...this.state.viewport} eventData={this.state}
          onClick={this.handleClick}
          height={'100vh'}
          width={'100vw'}
          mapboxApiAccessToken={process.env.MAPBOX_ACCESS_TOKEN}
          onViewportChange={(viewport) => this.setState({ viewport })}
        >
          {gigs.results.map(i => (
            <Marker
              key={i.id}
              latitude={i.venue.latitude}
              longitude={i.venue.longitude}
            >
              {/* () => this.setState({ eventname: i.eventname }), this.showInfo */}
              <div {...i} name={i} onClick={() => this.showInfo(i)}>
                <img className='pin' src={i.imageurl} />
              </div>
            </Marker>
          ))}
        </ReactMapGL>        
```

As each event from Skiddle came with a location specified by latitude and longitude, these were used as the required data to render the data onto the map
<br />
For the markers used on the map, we used the image data provided by Skiddle


As we worked in pairs from one laptop for the duration, we sat side by side and worked on every step together 
<br />
In previous tasks we would work with listing data onto an index page as a list.  The above code snippet shows our dropdown listed data that populates when an event is clicked.  The listed data was set in state so we were able to call it as it was named in the API and render each one using HTML elements semantically.


# What would we work on next? #
An idea would be to work on allowing users to filter or search as an option.  It was an idea that we considered but as we only had 48 hours, we worked on achieving MVP.
