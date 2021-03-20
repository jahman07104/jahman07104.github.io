---
layout: post
title:      " A Coding Process that demonstrates the essence of react"
date:       2021-03-20 10:51:35 -0400
permalink:  a_coding_process_that_demonstrates_the_essence_of_react
---


The task at hand is to add a search input 
to choose a profile by name. 
In other words type the name and have that profile appear.
The App is already built and connected to the redux store
First thing to do is decide
where to begin..
what component..??
The home page is the component  that renders the profiles to the page.. in the div on line 32 ..so I will start there

here is the code that rendered it to the screen 

import React, { useEffect } from "react";
import Card from "../components/card";
import Navbar from "./Navbar";
import Footer from "../components/Footer";
import { connect } from "react-redux";
import { getProfiles } from "../actionCreator/setProfiles";
import store from "../store";

const Home = (props) => {
  useEffect(() => {
    store.dispatch(getProfiles());
  }, []);


const profileItems = props.profiles.profiles.map((profile, index) => {

    return (

      <Card

        id={profile.id}
        name={profile.name}
        email={profile.email}
        city={profile.city}
				phone={profile.phone}
        avatar={profile.image}
        rating={profile.rating}
			  key={index}
        / >
    );
 });

return (
    <div className='container'>

   <Navbar title='Profile viewer' icon='fab fa-forumbee' />
    <div className='row'>{profileItems}</div>
      <br></br>
      <div
        style={{ borderTop: "2px solid #fff ", marginLeft: 4, marginRight: 4 }}
      ></div>
      <Footer year={new Date().getFullYear()} />
    </div>
  );

};
const mapStateToProps = (state) => ({
  profiles: state.profiles,
});
export default connect(mapStateToProps)(Home);

I have to start making my plan before I start coding to formulate an approach
what type of search input ..??
I will just use a simple text input

<input type=" text" />

I will neeed an eventlistener for my input field as that 
event will trigger a change in state that will in turn trigger 
a re-rendering of the dom which will get me closer to my goal of displaying my selected proifle

I will also need to need to address state and therfore will use the setState hook 
so I write a hook to set name state

  const [name, setName ] = useState("")

I am using state and setstate because as I type in the input the state of the component will change to update to the profiles that I am filtering through 
I will have to add usestate to react

now I have to decide
what methods will I need to use to search all
my profiles and to select them based on their names

I will put in a console.log to find out what type of data I am working with to help determine what kind of method to use

{console.log(profileItems}
*** note to self  *calling props on an aray will return undefined
that returns a react elements that are an array of objects *

I realize I have to update the input type to reflect state changes to the name

<input type=" text" onChange{(e) => setName(e.target.value)}/>

I got an error " setname is not defined.."
added useState to react
error cleared

search bar on screen no funtuality
add a function to update the state
warning name is assigned but not used
but profiles renderd..no immediate need to persue

again formulate a plan focus on task ..  
what type of data do I have to work with..??
that will detemine what methods I use
I have an array of objects
what array method will best give me the outcome I need
I determined I need a filter method
and an include method to compare strings to see if the letter I type in is included in the profile names

check MDN for filter and include methods and the syntaxes and if they apply
Both methods look promising I will then ammend my card rendition 

 let profileItems = props.profiles.profiles.filter((profile) => profile.name.includes(name)).map((profile, index) => {
    
    return (
      <Card
        id={profile.id}
 
      </div>

success but not case sensitive..need to add the lowerCase() function

  let profileItems = props.profiles.profiles.filter((profile) => profile.name.toLowerCase().includes(name)).map((profile, index) => {
    
    return (
      <Card
        id={profile.id}

task accomplished ..
I am able to filter my profiles by name and it is lowercase sensitive

