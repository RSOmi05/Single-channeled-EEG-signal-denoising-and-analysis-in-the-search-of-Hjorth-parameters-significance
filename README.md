# Single channeled EEG signal denoising and analysis in the search of Hjorth parameters significance
Plotting the given EEG signal in the time domain (both number of samples and time are plotted on the x-axis, whereas signal amplitude is on the y-axis in voltage) has demonstrated the changes of the brain’s electrical activity over time (190 seconds), illustrated in Figure 1 (green). In contrast, the given EEG signal in the frequency domain (plotted with frequency in Hz on the x-axis and corresponding power spectral density on the y-axis in voltage) is shown in Figure 2 (red). I chose to plot the EEG signal in the frequency domain using the Power Spectral Density (PSD) because PSD quantifies signal power (numerical representation of the strength) across frequencies, rather than simply displaying raw frequency amplitudes. While FFT plots alone are noisier and less interpretable, PSD estimation methods like Welch's method average multiple short segments of the data, resulting in a significant reduction of variance and noise. This task was addressed using Python within the Jupyter Notebook because of its flexibility, scalability, and integration with modern machine learning and data science tools.

Figure 1. Single-channeled EEG Signal in time domain, shown in both time (seconds) and number of samples
The original EEG signal (shown in red) maintains a relatively consistent power level across higher frequency bands, indicative of interference and unwanted artifacts, as shown in Figure 2(red components). 

Figure 2 Given Single-channeled EEG Signal in the frequency domain

2 (b). Noise Removal from the given EEG signal
Figure 3 illustrates the plot of the original EEG signal and the filtered EEG signal after noise removal using the required filters. To filter the given signal, I applied a combination of band-pass and notch filtering techniques for effective noise removal. Initially, a bandpass filter with a range of 0.5 Hz (as the low-cutoff frequency) to 30 Hz (as the high-cutoff frequency) was used to preserve essential EEG frequencies, while excluding irrelevant slow drifts and high-frequency muscular interference. Additionally, a notch filter at 50 Hz was implemented to specifically eliminate power-line interference, which is prevalent in electrical systems in Bangladesh. These filtering methods are crucial as they significantly enhance the signal's clarity and biological interpretability by retaining critical neurological information while eliminating confounding artifacts. 

Figure 3. Demonstration of (a) original EEG signal and (b) filtered EEG signal after noise removal using filters in the time domain.   

Figure 4 illustrates a comparative overview of the power spectral density of the original EEG signal and its corresponding filtered one in the frequency domain. This graph clearly depicts that filtering significantly reduced noise and irrelevant frequencies from the EEG signal. 
The original EEG signal (shown in red) has a relatively consistent power level across higher frequency bands, indicative of interference and unwanted artifacts. Conversely, the filtered EEG signal (shown in purple) demonstrates a sharp reduction in power at frequencies beyond 30 Hz due to the applied band-pass filter. This clearly reflects effective elimination of high-frequency noise and other artifacts, leaving a clean representation of the relevant EEG frequencies within the biologically meaningful range (below 30 Hz). Such refined signals greatly improve the reliability and interpretability of subsequent EEG analyses.


Figure. 4: Comparison between original and filtered EEG signal in the Frequency Domain.
2 (c). Make 5-second segments to the signal and plot the average (mean) of all the segments (Total 190 sec data is provided; sampling rate=128 Hz)

Figure. 5: (a) Average amplitude of each 5-second EEG segment over 190 seconds signal, (b) Average EEG waveform (mean of 38 * 5-second segments).
The graphs provide insights into the average amplitude behavior of EEG segments over time. The top plot, Figure 5(a) displays the mean amplitude for each 5-second segment among a total of 38 segments, revealing overall stability with minor fluctuations, except for a noticeable drop around segment 21, which may suggest an artifact or transient disruption in the signal.  
Whereas the lower plot, Figure 5(b) shows the average waveform of a single 5-second segment by aligning all these 38 segments on top of each other (sample by sample) and then calculating the mean amplitude at each corresponding single point across 38 segments. This average waveform retains key oscillatory patterns while reducing random noise, providing a clearer picture of the brain’s consistent rhythmic behavior during the recording period. Together, these visualizations highlight both the temporal dynamics and the stability of the EEG signal.
2 (d). Is there any significant difference in Hjorth parameters (Activity, Mobility, and Complexity) between the odd segments and even segments?
Three of the Hjorth parameters including activity, mobility, and complexity) between the odd segments and even segments of the given EEG signal are listed in Table 1, whereas the paired t-test between those two segments is listed in Table 2.
Table 1. Hjorth parameters for odd and even segments

Odd Segment	Even Segment
Segment	Activity	Mobility	Complexity	Segment	Activity	Mobility	Complexity
1	860.4503	0.268498	4.204849	1	1113.642	0.251505	4.692283
2	529.07	0.272673	4.242557	2	1964.543	0.17609	5.403037
3	317.2907	0.326501	3.795483	3	1262.134	0.215357	5.337589
4	183.386	0.406261	3.11641	4	934.7228	0.242352	4.833978
5	487.0742	0.277197	4.21194	5	680.5158	0.247812	4.387972
6	1187.78	0.222882	5.458399	6	1269.296	0.184747	5.731913
7	973.3132	0.193041	5.870823	7	1056.859	0.200497	4.973885
8	306.495	0.311212	3.826124	8	476.4078	0.266558	4.140586
9	1205.865	0.212206	4.474304	9	872.6721	0.22618	4.657024
10	438.3374	0.297776	3.852834	10	1229.025	0.234078	5.419829
11	738.7149	0.348922	3.651092	11	1082.311	0.223946	5.289211
12	216.0869	0.419201	3.01872	12	526.0594	0.274657	4.194065
13	419.9085	0.304488	3.848035	13	432.349	0.290949	4.106431
14	162.3759	0.472611	2.684879	14	627.9989	0.252597	4.594999
15	182.3881	0.443122	2.872875	15	174.8918	0.413739	2.98246
16	249.1125	0.35806	3.242872	16	327.9425	0.318754	3.696381
17	491.5951	0.246056	4.257931	17	78.5499	0.578084	2.117071
18	1131.141	0.258307	4.23118	18	1330.358	0.181314	6.481535
19	884.664	0.372203	3.689123	19	1089.272	0.236618	4.927231

Table 2. Statistical test (paired t-test) between odd and even segments

Parameter	t-statistic	p-value	Significance (p = 0.05)
Activity	-2.1472	0.038588	Significant
Mobility	1.8564	0.071596	Not Significant
Complexity	-2.4095	0.0212135	Significant


There is a significant difference in two of the three Hjorth parameters between odd and even segments, which are activity and complexity. P value for activity was 0.038588 (significant at p < 0.05), suggesting variations in signal amplitude and power distribution across these segments, whereas p-value for complexity was 0.0212135 (significant at p < 0.05), indicating variability in signal dynamics between odd and even segments. Mobility, however, does not show a significant difference (p = 0.071596), which suggests that variations in signal variance and shape complexity are more sensitive to the segmentation than frequency-related characteristics.
e. Is there any significance among Hjorth parameters (Activity, Mobility, and Complexity) for all segments (38 segments)?

Each Hjorth parameter across all segments is visualized distinctly, highlighting variability among segments, as shown in Figure 6.

Figure 6: Activity, mobility, and complexity per segment across 190 secs data (total 38 segments) 

Finding out significance among the Hjorth parameters (Activity, Mobility, and Complexity) for all segments (38 segments) typically requires additional statistical testing, like an ANOVA test to confirm segment-level differences. To conduct an ANOVA test, all segments are divided into four groups:
Group 1: Segments 1-10 (early recording period)
Group 2: Segments 11-20 (early-mid recording period)
Group 3: Segments 21-30 (mid-late recording period)
Group 4: Segments 31-38 (late recording period)

Table 3. Repeated-Measures ANOVA (One-Way) Among Hjorth Parameters across All Segments

Parameter	F-value	Effect Size (η²)	p-value	Significance
(p = 0.05)	Mean of Group 1	Mean of Group 2	Mean of Group 3	Mean of Group 4
Activity	2.178	0.161	0.109	Not Significant	833.28	901.61	456.31	697.83
Mobility	3.550	0.239	0.024	Significant	0.2684	0.2349	0.3444	0.3187
Complexity	2.797	0.198	0.055	Not Significant	4.4226	4.8406	3.7243	4.0804

Unlike statistical t-test, only the mobility parameter shows statistically significant differences between sequential groups (p = 0.024), suggesting significant temporal changes in the frequency characteristics of the EEG signal during the recording session across all 38 segments. Group 3 shows highest mean mobility and variability, where temporal transition occurs around segment 20-21. 


Figure. 7: Distribution of Hjorth parameters by four sequential groups and their group means comparision 

In terms of activity parameter, the highest variability was found in Group 1, whereas Group 3 shows consistently lower activity levels. Besides, complexity parameters showed inverse relationship pattern compared to mobility and moderate inter-group variability. Whereas group 2 shows peak complexity values, on the other hand, group 3 demonstrates the lowest complexity (simplest waveforms). 
Figure 7 demonstrates the Hjorth parameters by four sequential groups across 38 segments, along with their calculated means across each group.  


