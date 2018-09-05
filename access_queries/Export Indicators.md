## Export Indicators

This query is used to export relevant fields to a single table.

```
SELECT UT_Data.Indicator_NId, UT_Indicator_en.Indicator_Name, UT_Data.Data_Value, UT_Unit_en.Unit_NId, UT_Unit_en.Unit_Name, UT_Area_en.Area_ID, UT_Area_en.Area_Name, UT_Area_Level_en.Area_Level_Name, UT_Area_en.Area_Level, UT_Indicator_Classifications_en.IC_Name, UT_Indicator_Classifications_en.Publisher, UT_TimePeriod.TimePeriod, UT_Subgroup_Vals_en.Subgroup_Val, UT_Subgroup_Type_en.Subgroup_Type_Name, UT_Area_Map_Layer.Layer_NId
FROM ((((UT_Area_Map_Layer INNER JOIN ((UT_Area_Level_en INNER JOIN (UT_Subgroup_Vals_en INNER JOIN (UT_Unit_en INNER JOIN (UT_Indicator_en INNER JOIN (UT_Indicator_Unit_Subgroup INNER JOIN (UT_TimePeriod INNER JOIN (UT_Indicator_Classifications_en INNER JOIN (UT_Area_en INNER JOIN UT_Data ON UT_Area_en.[Area_NId] = UT_Data.[Area_NId]) ON UT_Indicator_Classifications_en.IC_NId = UT_Data.Source_NId) ON UT_TimePeriod.TimePeriod_NId = UT_Data.TimePeriod_NId) ON UT_Indicator_Unit_Subgroup.IUSNId = UT_Data.IUSNId) ON UT_Indicator_en.Indicator_NId = UT_Indicator_Unit_Subgroup.Indicator_NId) ON UT_Unit_en.Unit_NId = UT_Indicator_Unit_Subgroup.Unit_NId) ON UT_Subgroup_Vals_en.Subgroup_Val_NId = UT_Indicator_Unit_Subgroup.Subgroup_Val_NId) ON UT_Area_Level_en.Area_Level = UT_Area_en.Area_Level) INNER JOIN UT_Area_Map ON UT_Area_en.Area_NId = UT_Area_Map.Area_NId) ON UT_Area_Map_Layer.Layer_NId = UT_Area_Map.Layer_NId) INNER JOIN UT_Area_Map_Metadata_en ON UT_Area_Map_Layer.Layer_NId = UT_Area_Map_Metadata_en.Layer_NId) INNER JOIN UT_Subgroup_Vals_Subgroup ON UT_Subgroup_Vals_en.Subgroup_Val_NId = UT_Subgroup_Vals_Subgroup.Subgroup_Val_NId) INNER JOIN UT_Subgroup_en ON UT_Subgroup_Vals_Subgroup.Subgroup_NId = UT_Subgroup_en.Subgroup_NId) INNER JOIN UT_Subgroup_Type_en ON UT_Subgroup_en.Subgroup_Type = UT_Subgroup_Type_en.Subgroup_Type_NId
ORDER BY UT_Data.Indicator_NId;
```