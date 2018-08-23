
## Gun Data CSV Data Clean Up


```python
# Import Dependencies
import pandas as pd
```


```python
# Load the csv
csv = "Data/gun-violence-data_.csv"
gun_data = pd.read_csv(csv)

# Preview the data
gun_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>incident_id</th>
      <th>date</th>
      <th>state</th>
      <th>city_or_county</th>
      <th>address</th>
      <th>n_killed</th>
      <th>n_injured</th>
      <th>incident_url</th>
      <th>source_url</th>
      <th>incident_url_fields_missing</th>
      <th>...</th>
      <th>participant_age</th>
      <th>participant_age_group</th>
      <th>participant_gender</th>
      <th>participant_name</th>
      <th>participant_relationship</th>
      <th>participant_status</th>
      <th>participant_type</th>
      <th>sources</th>
      <th>state_house_district</th>
      <th>state_senate_district</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>461105</td>
      <td>2013-01-01</td>
      <td>Pennsylvania</td>
      <td>Mckeesport</td>
      <td>1506 Versailles Avenue and Coursin Street</td>
      <td>0</td>
      <td>4</td>
      <td>http://www.gunviolencearchive.org/incident/461105</td>
      <td>http://www.post-gazette.com/local/south/2013/0...</td>
      <td>False</td>
      <td>...</td>
      <td>0::20</td>
      <td>0::Adult 18+||1::Adult 18+||2::Adult 18+||3::A...</td>
      <td>0::Male||1::Male||3::Male||4::Female</td>
      <td>0::Julian Sims</td>
      <td>NaN</td>
      <td>0::Arrested||1::Injured||2::Injured||3::Injure...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://pittsburgh.cbslocal.com/2013/01/01/4-pe...</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>460726</td>
      <td>2013-01-01</td>
      <td>California</td>
      <td>Hawthorne</td>
      <td>13500 block of Cerise Avenue</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/460726</td>
      <td>http://www.dailybulletin.com/article/zz/201301...</td>
      <td>False</td>
      <td>...</td>
      <td>0::20</td>
      <td>0::Adult 18+||1::Adult 18+||2::Adult 18+||3::A...</td>
      <td>0::Male</td>
      <td>0::Bernard Gillis</td>
      <td>NaN</td>
      <td>0::Killed||1::Injured||2::Injured||3::Injured</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://losangeles.cbslocal.com/2013/01/01/man-...</td>
      <td>62.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>478855</td>
      <td>2013-01-01</td>
      <td>Ohio</td>
      <td>Lorain</td>
      <td>1776 East 28th Street</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/478855</td>
      <td>http://chronicle.northcoastnow.com/2013/02/14/...</td>
      <td>False</td>
      <td>...</td>
      <td>0::25||1::31||2::33||3::34||4::33</td>
      <td>0::Adult 18+||1::Adult 18+||2::Adult 18+||3::A...</td>
      <td>0::Male||1::Male||2::Male||3::Male||4::Male</td>
      <td>0::Damien Bell||1::Desmen Noble||2::Herman Sea...</td>
      <td>NaN</td>
      <td>0::Injured, Unharmed, Arrested||1::Unharmed, A...</td>
      <td>0::Subject-Suspect||1::Subject-Suspect||2::Vic...</td>
      <td>http://www.morningjournal.com/general-news/201...</td>
      <td>56.0</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>478925</td>
      <td>2013-01-05</td>
      <td>Colorado</td>
      <td>Aurora</td>
      <td>16000 block of East Ithaca Place</td>
      <td>4</td>
      <td>0</td>
      <td>http://www.gunviolencearchive.org/incident/478925</td>
      <td>http://www.dailydemocrat.com/20130106/aurora-s...</td>
      <td>False</td>
      <td>...</td>
      <td>0::29||1::33||2::56||3::33</td>
      <td>0::Adult 18+||1::Adult 18+||2::Adult 18+||3::A...</td>
      <td>0::Female||1::Male||2::Male||3::Male</td>
      <td>0::Stacie Philbrook||1::Christopher Ratliffe||...</td>
      <td>NaN</td>
      <td>0::Killed||1::Killed||2::Killed||3::Killed</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://denver.cbslocal.com/2013/01/06/officer-...</td>
      <td>40.0</td>
      <td>28.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>478959</td>
      <td>2013-01-07</td>
      <td>North Carolina</td>
      <td>Greensboro</td>
      <td>307 Mourning Dove Terrace</td>
      <td>2</td>
      <td>2</td>
      <td>http://www.gunviolencearchive.org/incident/478959</td>
      <td>http://www.journalnow.com/news/local/article_d...</td>
      <td>False</td>
      <td>...</td>
      <td>0::18||1::46||2::14||3::47</td>
      <td>0::Adult 18+||1::Adult 18+||2::Teen 12-17||3::...</td>
      <td>0::Female||1::Male||2::Male||3::Female</td>
      <td>0::Danielle Imani Jameison||1::Maurice Eugene ...</td>
      <td>3::Family</td>
      <td>0::Injured||1::Injured||2::Killed||3::Killed</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://myfox8.com/2013/01/08/update-mother-sho...</td>
      <td>62.0</td>
      <td>27.0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 29 columns</p>
</div>




```python
# Clean up participant gender data

gun_data["participant_gender"] = gun_data["participant_gender"].fillna("0::Unknown")


def clean_participant_gender(row) :
    gender_row_values = []
    gender_row = str(row).split("||")
    for x in gender_row :
        gender_row_value = str(x).split("::")
        if len(gender_row_value) > 1 :
            gender_row_values.append(gender_row_value[1])
            
    return gender_row_values


participant_genders = gun_data.participant_gender.apply(clean_participant_gender)
gun_data["participant_gender_total"] = participant_genders.apply(lambda x: len(x))
gun_data["participant_gender_male"] = participant_genders.apply(lambda x: x.count("Male"))
gun_data["participant_gender_female"] = participant_genders.apply(lambda x: x.count("Female"))
gun_data["participant_gender_unknown"] = participant_genders.apply(lambda x: x.count("Unknown"))
del(participant_genders)
gun_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>incident_id</th>
      <th>date</th>
      <th>state</th>
      <th>city_or_county</th>
      <th>address</th>
      <th>n_killed</th>
      <th>n_injured</th>
      <th>incident_url</th>
      <th>source_url</th>
      <th>incident_url_fields_missing</th>
      <th>...</th>
      <th>participant_relationship</th>
      <th>participant_status</th>
      <th>participant_type</th>
      <th>sources</th>
      <th>state_house_district</th>
      <th>state_senate_district</th>
      <th>participant_gender_total</th>
      <th>participant_gender_male</th>
      <th>participant_gender_female</th>
      <th>participant_gender_unknown</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>461105</td>
      <td>2013-01-01</td>
      <td>Pennsylvania</td>
      <td>Mckeesport</td>
      <td>1506 Versailles Avenue and Coursin Street</td>
      <td>0</td>
      <td>4</td>
      <td>http://www.gunviolencearchive.org/incident/461105</td>
      <td>http://www.post-gazette.com/local/south/2013/0...</td>
      <td>False</td>
      <td>...</td>
      <td>NaN</td>
      <td>0::Arrested||1::Injured||2::Injured||3::Injure...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://pittsburgh.cbslocal.com/2013/01/01/4-pe...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>460726</td>
      <td>2013-01-01</td>
      <td>California</td>
      <td>Hawthorne</td>
      <td>13500 block of Cerise Avenue</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/460726</td>
      <td>http://www.dailybulletin.com/article/zz/201301...</td>
      <td>False</td>
      <td>...</td>
      <td>NaN</td>
      <td>0::Killed||1::Injured||2::Injured||3::Injured</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://losangeles.cbslocal.com/2013/01/01/man-...</td>
      <td>62.0</td>
      <td>35.0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>478855</td>
      <td>2013-01-01</td>
      <td>Ohio</td>
      <td>Lorain</td>
      <td>1776 East 28th Street</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/478855</td>
      <td>http://chronicle.northcoastnow.com/2013/02/14/...</td>
      <td>False</td>
      <td>...</td>
      <td>NaN</td>
      <td>0::Injured, Unharmed, Arrested||1::Unharmed, A...</td>
      <td>0::Subject-Suspect||1::Subject-Suspect||2::Vic...</td>
      <td>http://www.morningjournal.com/general-news/201...</td>
      <td>56.0</td>
      <td>13.0</td>
      <td>5</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>478925</td>
      <td>2013-01-05</td>
      <td>Colorado</td>
      <td>Aurora</td>
      <td>16000 block of East Ithaca Place</td>
      <td>4</td>
      <td>0</td>
      <td>http://www.gunviolencearchive.org/incident/478925</td>
      <td>http://www.dailydemocrat.com/20130106/aurora-s...</td>
      <td>False</td>
      <td>...</td>
      <td>NaN</td>
      <td>0::Killed||1::Killed||2::Killed||3::Killed</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://denver.cbslocal.com/2013/01/06/officer-...</td>
      <td>40.0</td>
      <td>28.0</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>478959</td>
      <td>2013-01-07</td>
      <td>North Carolina</td>
      <td>Greensboro</td>
      <td>307 Mourning Dove Terrace</td>
      <td>2</td>
      <td>2</td>
      <td>http://www.gunviolencearchive.org/incident/478959</td>
      <td>http://www.journalnow.com/news/local/article_d...</td>
      <td>False</td>
      <td>...</td>
      <td>3::Family</td>
      <td>0::Injured||1::Injured||2::Killed||3::Killed</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://myfox8.com/2013/01/08/update-mother-sho...</td>
      <td>62.0</td>
      <td>27.0</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 33 columns</p>
</div>




```python
# Clean up n_guns and gun_stolen data

gun_data["n_guns_involved"] = gun_data["n_guns_involved"].fillna(0)
gun_data["gun_stolen"] = gun_data["gun_stolen"].fillna("0::Unknown")
# Prints a lot but gives all the unique values of a column
#dataset_gunviolence["gun_stolen"].unique()

def clean_gun_stolen(row) :
    unknownCount = 0
    stolenCount = 0
    notstolenCount = 0
    gunstolen_row_values = []
    
    gunstolen_row = str(row).split("||")
    for x in gunstolen_row :
            gunstolen_row_value = str(x).split("::")
            if len(gunstolen_row_value) > 1 :
                gunstolen_row_values.append(gunstolen_row_value[1])
                if "Stolen" in gunstolen_row_value :
                    stolenCount += 1
                elif "Not-stolen" in gunstolen_row_value :
                    notstolenCount += 1
                else :
                    unknownCount += 1
                    
    return gunstolen_row_values


gunstolenvalues = gun_data.gun_stolen.apply(clean_gun_stolen)
gun_data["gun_stolen_stolen"] = gunstolenvalues.apply(lambda x: x.count("Stolen"))
gun_data["gun_stolen_notstolen"] = gunstolenvalues.apply(lambda x: x.count("Not-stolen"))
del(gunstolenvalues)

gun_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>incident_id</th>
      <th>date</th>
      <th>state</th>
      <th>city_or_county</th>
      <th>address</th>
      <th>n_killed</th>
      <th>n_injured</th>
      <th>incident_url</th>
      <th>source_url</th>
      <th>incident_url_fields_missing</th>
      <th>...</th>
      <th>participant_type</th>
      <th>sources</th>
      <th>state_house_district</th>
      <th>state_senate_district</th>
      <th>participant_gender_total</th>
      <th>participant_gender_male</th>
      <th>participant_gender_female</th>
      <th>participant_gender_unknown</th>
      <th>gun_stolen_stolen</th>
      <th>gun_stolen_notstolen</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>461105</td>
      <td>2013-01-01</td>
      <td>Pennsylvania</td>
      <td>Mckeesport</td>
      <td>1506 Versailles Avenue and Coursin Street</td>
      <td>0</td>
      <td>4</td>
      <td>http://www.gunviolencearchive.org/incident/461105</td>
      <td>http://www.post-gazette.com/local/south/2013/0...</td>
      <td>False</td>
      <td>...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://pittsburgh.cbslocal.com/2013/01/01/4-pe...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>460726</td>
      <td>2013-01-01</td>
      <td>California</td>
      <td>Hawthorne</td>
      <td>13500 block of Cerise Avenue</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/460726</td>
      <td>http://www.dailybulletin.com/article/zz/201301...</td>
      <td>False</td>
      <td>...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Victim||4:...</td>
      <td>http://losangeles.cbslocal.com/2013/01/01/man-...</td>
      <td>62.0</td>
      <td>35.0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>478855</td>
      <td>2013-01-01</td>
      <td>Ohio</td>
      <td>Lorain</td>
      <td>1776 East 28th Street</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/478855</td>
      <td>http://chronicle.northcoastnow.com/2013/02/14/...</td>
      <td>False</td>
      <td>...</td>
      <td>0::Subject-Suspect||1::Subject-Suspect||2::Vic...</td>
      <td>http://www.morningjournal.com/general-news/201...</td>
      <td>56.0</td>
      <td>13.0</td>
      <td>5</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>478925</td>
      <td>2013-01-05</td>
      <td>Colorado</td>
      <td>Aurora</td>
      <td>16000 block of East Ithaca Place</td>
      <td>4</td>
      <td>0</td>
      <td>http://www.gunviolencearchive.org/incident/478925</td>
      <td>http://www.dailydemocrat.com/20130106/aurora-s...</td>
      <td>False</td>
      <td>...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://denver.cbslocal.com/2013/01/06/officer-...</td>
      <td>40.0</td>
      <td>28.0</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>478959</td>
      <td>2013-01-07</td>
      <td>North Carolina</td>
      <td>Greensboro</td>
      <td>307 Mourning Dove Terrace</td>
      <td>2</td>
      <td>2</td>
      <td>http://www.gunviolencearchive.org/incident/478959</td>
      <td>http://www.journalnow.com/news/local/article_d...</td>
      <td>False</td>
      <td>...</td>
      <td>0::Victim||1::Victim||2::Victim||3::Subject-Su...</td>
      <td>http://myfox8.com/2013/01/08/update-mother-sho...</td>
      <td>62.0</td>
      <td>27.0</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 35 columns</p>
</div>




```python
# Clean up participant_age_group data

gun_data["participant_age_group"] = gun_data["participant_age_group"].fillna("0::Unknown")

def clean_participant_age_group(row) :
    unknownCount = 0
    childCount = 0
    teenCount = 0
    adultCount = 0
    agegroup_row_values = []
    
    agegroup_row = str(row).split("||")
    for x in agegroup_row :
        agegroup_row_value = str(x).split("::")
        if len(agegroup_row_value) > 1 :
            agegroup_row_values.append(agegroup_row_value[1])
            if "Child 0-11" in agegroup_row_value :
                childCount += 1
            elif "Teen 12-17" in agegroup_row_value :
                teenCount += 1
            elif "Adult 18+" in agegroup_row_value :
                adultCount += 1
            else :
                unknownCount += 1
                
    return agegroup_row_values

agegroupvalues = gun_data.participant_age_group.apply(clean_participant_age_group)
gun_data["agegroup_child"] = agegroupvalues.apply(lambda x: x.count("Child 0-11"))
gun_data["agegroup_teen"] = agegroupvalues.apply(lambda x: x.count("Teen 12-17"))
gun_data["agegroup_adult"] = agegroupvalues.apply(lambda x: x.count("Adult 18+"))
del(agegroupvalues)

gun_data.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>incident_id</th>
      <th>date</th>
      <th>state</th>
      <th>city_or_county</th>
      <th>address</th>
      <th>n_killed</th>
      <th>n_injured</th>
      <th>incident_url</th>
      <th>source_url</th>
      <th>incident_url_fields_missing</th>
      <th>...</th>
      <th>state_senate_district</th>
      <th>participant_gender_total</th>
      <th>participant_gender_male</th>
      <th>participant_gender_female</th>
      <th>participant_gender_unknown</th>
      <th>gun_stolen_stolen</th>
      <th>gun_stolen_notstolen</th>
      <th>agegroup_child</th>
      <th>agegroup_teen</th>
      <th>agegroup_adult</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>461105</td>
      <td>2013-01-01</td>
      <td>Pennsylvania</td>
      <td>Mckeesport</td>
      <td>1506 Versailles Avenue and Coursin Street</td>
      <td>0</td>
      <td>4</td>
      <td>http://www.gunviolencearchive.org/incident/461105</td>
      <td>http://www.post-gazette.com/local/south/2013/0...</td>
      <td>False</td>
      <td>...</td>
      <td>NaN</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>460726</td>
      <td>2013-01-01</td>
      <td>California</td>
      <td>Hawthorne</td>
      <td>13500 block of Cerise Avenue</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/460726</td>
      <td>http://www.dailybulletin.com/article/zz/201301...</td>
      <td>False</td>
      <td>...</td>
      <td>35.0</td>
      <td>1</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>478855</td>
      <td>2013-01-01</td>
      <td>Ohio</td>
      <td>Lorain</td>
      <td>1776 East 28th Street</td>
      <td>1</td>
      <td>3</td>
      <td>http://www.gunviolencearchive.org/incident/478855</td>
      <td>http://chronicle.northcoastnow.com/2013/02/14/...</td>
      <td>False</td>
      <td>...</td>
      <td>13.0</td>
      <td>5</td>
      <td>5</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>478925</td>
      <td>2013-01-05</td>
      <td>Colorado</td>
      <td>Aurora</td>
      <td>16000 block of East Ithaca Place</td>
      <td>4</td>
      <td>0</td>
      <td>http://www.gunviolencearchive.org/incident/478925</td>
      <td>http://www.dailydemocrat.com/20130106/aurora-s...</td>
      <td>False</td>
      <td>...</td>
      <td>28.0</td>
      <td>4</td>
      <td>3</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>4</th>
      <td>478959</td>
      <td>2013-01-07</td>
      <td>North Carolina</td>
      <td>Greensboro</td>
      <td>307 Mourning Dove Terrace</td>
      <td>2</td>
      <td>2</td>
      <td>http://www.gunviolencearchive.org/incident/478959</td>
      <td>http://www.journalnow.com/news/local/article_d...</td>
      <td>False</td>
      <td>...</td>
      <td>27.0</td>
      <td>4</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 38 columns</p>
</div>




```python
# Save dataframe as new file
gun_data.to_csv("Data/clean_gun_data.csv")
```
