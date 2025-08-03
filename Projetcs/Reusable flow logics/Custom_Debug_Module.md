Input Data passing from Main Flow

Common.Custom Data = Append("Entered flow: ", Flow.FlowName) ==>  Entered flow : Collateral Tracking

Common.Flowname  = flow.flowname ==> Collateral Tracking 

Common.flowstep - static value : 14 here

Common.FlowlOgging Level = flow.flowlogging level - 0 - This we set in first Update data

Common.MessageLogging level = 0

Common.Debug attribute name = Debug log

Common.flowVersion = flow.flowversion - Its system Defined






Common Module flow


	1. First we doing sanity , ie If Debug Attribute name is not set or empty we are setting it as "DebugLog" , If it has value keep the existing value




	• Common. DebugAttributeName : if(IsNotSetOrEmpty(Common.DebugAttributeName),"DebugLog",Common.DebugAttributeName)

Similarly 

	• Common. MessageLoggingLevel : if(IsNotSetOrEmpty(Common.MessageLoggingLevel),0,Common.MessageLoggingLevel)

	• Common.FlowLoggingLevel : if(IsNotSetOrEmpty(Common.FlowLoggingLevel),0,Common.FlowLoggingLevel)


	2. Then we are checking the Logging level , If Message Logging Level is >= Flow.Logging Level , Then only we are saving the debug values . If not we will skip the debug module 

	Common.MessageLoggingLevel >= Common.FlowLoggingLevel
	
	3. Get Particpant Data

	Common.DebugAttributeName : Task. DebugLog
	
	
	This means the value is we stored in Common.DebugAttributeName (Ie, DebugLog) will now assign to Task.Debuglog
	
	
	
	
	4. Update Data - TimeStamp


	• We are saving current utc date time into a variable Common.TimeStamp

Common.TimeStamp : GetCurrentDateutc()





	5. Update Data - LogString

Task.LogString : Append(ToString(Common.TimeStamp), "--", Common.FlowName, "-", "v", Common.FlowVersion, "-", "Step:", ToString(Common.FlowStep), "-->", Common.CustomData, "\r")

2025-05-16T19:47:29.309Z--Collateral Tracking-v5.0-Step:14-->Entered flow: Collateral Tracking



<img width="1735" height="4590" alt="image" src="https://github.com/user-attachments/assets/97016954-08e0-46f7-abb5-b5157a616ca4" />
