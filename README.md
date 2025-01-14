<h1>EMD_Analysis</h1>
Script to measure electrical mechanical delay (EMG onset - Force onset)
Written in the language used by the DAQ (CED Spike)

<h4>Note on the use of this script</h4>
<i>A substantial amount of time and effort has been put into the development of this script and it is being offered free to use by anyone within the research community. However, it is expected that anyone making use of it acknowledges that in an appropriate manner, e.g. if you publish research for which this script's use has played a substantial role in the analysis of the data, then it asked that the scripts author, Dr Jon Kelly is included in the papers list of authors. If the script as provided plays a more minor role, for example, if you substantially modified it or only minor parts of the data were analysed with it, an acknowledgement is still appreciated.
The script is being made available out of good will to fellow researchers, please don't abuse that.
If you have queries or requests for the scripts development or would like to do some work on its development, please contact the scripts author on: <a href=mailto:jon.kelly@tuta.io>jon.kelly@tuta.io</a></i>
     
<h2>Overview of the scripts operation</h2>
Notes
    • This guide is intended for researchers with existing knowledge in the area of EMG analysis and so commonly used terms and concepts in this field are not explained. Other texts should be referred to where any clarification is required.
Settings
    • The values in the default settings file provided with this script should work well with most data and these are automatically loaded when the script is started provided the settings file is correctly named and in the same folder as the script. 
    • Custom settings file can be created and loaded from within the script. 
    • If different default settings are required, then a modified settings file can be used to replace the original by simply saving in the same folder with the default file name (EMDCalcDefStn.txt). Users are strongly advised to keep a copy of the original default settings file elsewhere.
    • For detailed explanation of settings, please refer to Appendix i in the User Guide.
Force onset detection
Force onsets are determined from a 3 stage process;
     1  Approximate force onsets are found by searching for the times when the force recorded exceeds a threshold value. This value is established by scanning at progressively lower thresholds to find the minimum that can be set whilst still finding the correct number of threshold crossings.
     
    
