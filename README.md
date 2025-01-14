<h1>EMD_Analysis</h1>
<p>Script to measure electrical mechanical delay (EMG onset - Force onset)</p>
<p>Written in the language used by the DAQ (CED Spike)</p>

<h4>Note on the use of this script</h4>
<p><i>A substantial amount of time and effort has been put into the development of this script and it is being offered free to use by anyone within the research community. However, it is expected that anyone making use of it acknowledges that in an appropriate manner, e.g. if you publish research for which this script's use has played a substantial role in the analysis of the data, then it asked that the scripts author, Dr Jon Kelly is included in the papers list of authors. If the script as provided plays a more minor role, for example, if you substantially modified it or only minor parts of the data were analysed with it, an acknowledgement is still appreciated.</p>
<p>The script is being made available out of good will to fellow researchers, please don't abuse that.
If you have queries or requests for the scripts development or would like to do some work on its development, please contact the scripts author on: <a href=mailto:jon.kelly@tuta.io>jon.kelly@tuta.io</a></i></p>

<p>For a flowchart outlining the structure of the scripts, see: EMD_Calc_flowchart.pdf</p>

<h2>Note</h2>
<p>This guide is intended for researchers with existing knowledge in the area of EMG analysis and so commonly used terms and concepts in this field are not explained. Other texts should be referred to where any clarification is required.</p>
     
<h2>Overview of the scripts operation</h2>
<p>This script is written to calculate electromechanicla delay i.e. the time difference between the onset of muscle electrical activity as recorded by electromyography (EMG) and the onset of the force from the resulting contraction. Very small delays (around 10ms) between muscle activation and force production can be clinically relevant.</p>

<p>This script is designed to be used on data where force and EMG are measured together within .smr data files from a CED DAQ based data collection setup.</p>

<h3>Stage 1:  Identify force onset</h3>
This is performed in 3 passes;
<ol>
     <li>This establishes approximate onset times by searching for threshold crossings. Repeatedly lower crossing threshold are set to establish the lowest threshold that can be set and return the expected number of repetitions of the contractios. These initial thresholds are intended only to give plausible time windows in which to perform more sensitive searched for force onsets which makes these searches less sensitive to noise.</li>
     <li>The second stage is to work backwards from the first pass estimated onsets. Standard deviations multiples of force signal amplitudes in quiescent periods prior to each pass 1 onset are used to set thresholds and the last high-going threshold crossing prior to the pass 1 onset is take as the second pass onset time.</li>
     <li>The final pass differentiates the force data to convert this to rate of force development (RoFD) and again use threshold crossings in a time window prior to the second pass onset times</li>
</ol>

<h3>Stage 2: Identify EMG onset times</h3>
<p>The force onset times are used to restrict the EMG search to physiologically plausible time windows prior to force onset. This reduces errors associated with noise. To make EMG activity more detacable against background noise (which can be several magnitudes larger) whilst still retaining temporal information, a time-frequency domain transform (TKEO) is performed on the EMG signal prior to analysis, which again uses threshold crossing times.</p>

<h4>EMD calculation</h4>
<p>EMD is calculated as the simple difference in time between EMG and force onset times. These data are saved to a CSV file. The script also annotates the results to indicate where it was not possible to find onsets within the defined parameters.</p>

<h2>Setting</h2>
<p>There are a large number of settings within the script intended to optimise its performance. The values in the default settings file are expected to work well with most data but it is likely that researchers will need to spend some time refining these to their particular data set to achieve optimal results.</p>
<p>Custom settings file can be created and loaded from within the script. If different default settings are required, then a modified settings file can be used to replace the original by simply saving in the same folder with the default file name (EMDCalcDefStn.txt). <b>Users are strongly advised to keep a copy of the original default settings file elsewhere.</b></p>

<p><b>For complete details of settings. See EMDSettingDetails.pdf</b></p>
