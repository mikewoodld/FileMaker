# Eos String Syntax for various things (non-OSC)

## Command Lines

  Turning A Channel On:

    <U1> $ chan 1 full full #
    
  
  Sneaking A Channel:

    <U1> $ chan 1 sneak #
       
         
  Turning A Group On:

    <U1> $ group 1 full full #

  
  Bringing A Channel to a certain level:

    <U1> $ group 1 at 57 #
  
  Changing Parameters

    <U1> $ chan 1 pan 32 tilt 40 #
    
  Clear Command Line:

    <U1> $ clear_cmd #
       
         
  Entering Patch (takes console to blind):

    <U1> $ patch #
    
 change the user number by changing the <U1> to whatever U number you want. The command will post to that user's command line. 


## Edit_Target


You can edit various target text fields using this syntax:

    <U#> Edit_Target <Field> <Target> <Number> <List Number> <Part Number> <Text> #
    

         Field: Label, Scene, Notes, Patch
  
         Target: Cue, Submaster, Macro, Snapshot (see next section for Palettes)
  
         Number: Target Number x 10,000
  
         List Number: List Number (if cue, otherwise -1)
  
         Part Number: Part Number (if part, otherwise -1)
  
         Text: The text to send
       
 For Example:
 
     <U1> Edit_Target Label Cue 50000 1 -1 Blackout #
     
          Will label List 1, Cue 5 (no parts) as "Blackout"
     
     
     
     <U1> Edit_Target Label Cue 60000 1 20 MARK #
     
          Will label List 1, Cue 6, Part 20 as "MARK"
 
 
 
 Editing Patch Information:
 
     <U1> Edit_Target Label Patch 901 -1 -1 House Light #
     
          Labeled channel 901 as "House Light" in the patch


     <U1> Edit_Target Notes Patch 2 -1 -1 Note Here #
     
          Added "note here" as the note for channel 2 in the patch
      
            
     <U1> Edit_Target Gel Patch 50 -1 -1 R80 #
     
          Set gel color to R80 for Channel 50 in Patch
          
     
     <U1> Edit_Target Text1 Patch 61 -1 -1 Front Cool #
     
          Set Text1 Database label in Patch for channel 61 to "Front Cool"
     
       
## Labeling Palettes      

    <U1> $ focus_palette 1 label TextHere # 
    <U1> $ intensity_palette 1 label TextHere # 
    <U1> $ color_palette 1 label TextHere # 
    <U1> $ beam_palette 1 label TextHere # 
      
  

## Forbidden Characters

You cannot use # (hashtag/pound sign/number sign, depending on your generation) in any text field, as EOS sees that symbol as the termination of a command. As far as I know, there is no way to escape this character, so it's best just to not use it. 


## Tips & Tricks

Take advantage of being able to specify a user number for your commands. Some things can happen in the background, others you want to see on your command lines. Perhaps plan a separate user just for your FM solution, and then show that command line on a magic sheet. 

## Why not OSC?

This is not a substitute for OSC at all, it's just slightly easier to implement in FileMaker, at least as of this writing. There aren't any specific OSC plugins for FileMaker (yet.) You can send strings that look like OSC to eos using the plugins we've talked about in these sessions (MonkeyBreadSoftware) - for example, you can send /eos/user/1/key/1 and it will push that key - but at this time, there are some issues with how EOS treats some arguments. You can't send labels reliably,for example. These things are being worked on. In my solution, I use a combination of these old fashioned strings as well as strings that look like OSC. For example, there's not a string command to take the console to blind, but you CAN say /eos/user/1/blind/ - so it's a bit of both for me. Eventually once some of these things are changed/fixed, I will update this document with that information. 

## Can I get data back into FM using this?

You can enable "String MSC Tx" to get some event data back in via String UDP, but that's beyond the scope of this document. OSC is the way to go for incoming data, but it's not a simple implementation right now. Since there is no FM OSC plugin, I rely on Scott Tusing's OSC ReRouter to help. https://github.com/sktusing/OSC-ReRouter

