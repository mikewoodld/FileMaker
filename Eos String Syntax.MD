# EOS String Syntax for various things (non-OSC)

## Command Lines

  Turning A Channel On:

    <U1> $ chan 1 full full #
    
  
  Sneaking A Channel:

    <U1> $ chan 1 sneak #
       
         
  Turning A Group On:

    <U1> $ group 1 full full #

  
  Bringing A Channel to a certain level:

    <U1> $ group 1 at 57 #
    
    
  Clear Command Line:

    <U1> $ clear_cmd #
       
         
  Entering Patch (takes console to blind):

    <U1> $ patch #


## Edit_Target

You can edit various target text fields using this syntax:

    <U#> Edit_Target <Field> <Target> <Number> <List Number> <Part Number> <Text>
    

         Field: Label, Scene, Notes, Patch
  
         Target: Cue, Submaster, Macro, ...
  
         Number: Target Number x 10,000
  
         List Number: List Number (if cue, otherwise -1)
  
         Part Number: Part Number (if part, otherwise -1)
  
         Text: The text to send
       
 For Example:
 
     <U1> Edit_Target Label Cue 50000 1 -1 Blackout
     
     Will label List 1, Cue 5 (no parts) as "Blackout"
     
     
     
     <U1> Edit_Target Label Cue 60000 1 20 MARK
     
     Will label List 1, Cue 6, Part 20 as "MARK"
 
 
 
 Editing Patch Information:
 
     <U1>Edit_Target Label Patch 901 -1 -1 House Light
     
     Labeled channel 901 as "House Light" in the patch


     <U1>Edit_Target Notes Patch 2 -1 -1 Note Here
     
     Added "note here" as the note for channel 2 in the patch
      
            
     <U1>Edit_Target Gel Patch 50 -1 -1 R80
     
     Set gel color to R80 for Channel 50 in Patch
          
     
     <U1>Edit_Target Text1 Patch 61 -1 -1 Front Cool
     
     Set Text1 Database label in Patch to "Front Cool"
     

## Forbidden Characters

You cannot use # (hashtag/pound sign/number sign, depending on your generation) in any text field, as EOS sees that symbol as the termination of a command. As far as I know, there is no way to escape this character, so it's best just to not use it. 
