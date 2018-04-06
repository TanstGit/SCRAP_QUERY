# SCRAP_QUERY
THE REPORT:
An SQL query which displays SCRAP_PART data for who what when and why

THE CURRENT ISSUE:
The report contains null values because it pulls from empty job keys due to the fact that those jobs were entered as tracking numbers which are registered as varchar rather than int.


ATTEMPT MADE:

select

  b.Part_No,
  c.Job_No,
  g.Job_No,   --ADDED TO JOIN JOB ON TRACKING NUMBER
  a.Tracking_No,
  a.Serial_No,
  a.Scrap_Reason,
  a.Report_Date,
  a.Scrap_Date,
  d.Workcenter_code,
  f.Workcenter_Group,
  c.Quantity as 'Order Quantity',  
  a.Quantity as 'Scrap Quantity',
  a.Net_Weight as 'Scrap lbs',  
  a.Unit_Cost,
  e.Last_Name,
  e.First_Name,  
  a.Extended_Cost

from Part_v_Scrap a                                                             
left join Part_v_Part b on a.Part_Key = b.Part_Key                              
left join Part_v_Job c on a.Job_Key = c.Job_Key                                 
left join Part_v_Workcenter d on a.Workcenter_Key = d.Workcenter_Key           
left join Plexus_Control_v_Plexus_User e on a.Recorded_By = e.Plexus_User_No    
left join Part_v_Workcenter f on a.Workcenter_Key = f.Workcenter_Key    F.Workcenter_Key

left join Part_v_Job g on a.Tracking_No = c.Job_Key  --ADDED to join JOB ON TRACKING NO


 where a.Scrap_Date between '04/1/2018' and '4/30/2018'    --SELECTS DATA IN A DATE RANGE
 order by a.scrap_Date,a.Serial_No                          


RESULT:

ERROR: CONVERSTION FAILED WHEN CONVERTING THE CARCHAR VALUE '12092-1' to data type int.






