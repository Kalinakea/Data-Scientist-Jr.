# Analysis of the opportunities for renewable energy in Mexico

<img src= "Pictures/Sener-renovables.jpg" width="300"> <img src= "Pictures/Captura%20de%20pantalla%202025-12-02%20193231.png" width="350"> <img src= "Pictures/Captura%20de%20pantalla%202025-12-02%20193547.png" width="300">

Nowadays, the overexploting of the non renewables resources are leading Mexico to take energetic alternatives for the lack of fosil fuels and global climate consecuenses.

Mexico is a country with great potential in geothermal energy, solar, eolic and hydraulic energy, but only 22% of national eletricity comes from renewable resources.
That´s why it has been made an analysis of every Mexico state comparing its energetic and economic potential, the fuel consumption and a comparation with other countries to create alternatives in the energetic field through graphs and machine learning models.

### Data cleaning
Dirty databases were used, so the cleaning must be done before any analysis or data manipulation. Mostly, these functions were used in every document but also every csv file was mannaged individually according to its requirement or particular needs.  
      def limpiar_indices(*args): 
        for i in range (len(df_dirty.columns)):
          df_dirty.columns.values[i] = (df_dirty.columns[i]).lower().replace(' ','_')
      
      def limpiar_strings(*nombres_col):
        for col in nombres_col:
          df_dirty[col] = df_dirty[col].str.lower()
      
      def limpiar_numeros_comas(*nombres_col):
        for col in nombres_col:
          df_dirty[col] = df_dirty[col].str.replace(',', '', regex=False)
          df_dirty[col] = pd.to_numeric(df_dirty[col], errors= 'coerce')
      
      def limpiar_numeros(*nombres_col):
        for col in nombres_col:
          df_dirty[col] = pd.to_numeric(df_dirty[col], errors= 'coerce')
      
      def llenar_vacios(*nombres_col):
        for col in nombres_col:
          df_dirty[col] = df_dirty[col].fillna(df_dirty[col].median()) 

The largest database used was the global energetic containing categories such as capacity, power sector emitions... for every type of energy (Hydro, Bioenergy, Renewables, Wind and Solar, Bioenergy, Nuclear). It has 357014 rows × 18 columns so it was a challenge to apply the correct filters according to the results and the conclutions that are wanted. A disperssion graph analysing capacity vs electricity generation, and it included just the top 14 most relevant countries for Mexico. Due to EEUU and China´s potential, it was necessary to create another disperssion graph in order to appreciate more clearly the difference between countries.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20234553.png" width=500> <img src="Pictures/Captura%20de%20pantalla%202025-12-04%20234616.png" width=500>

Machine Learning tools were used, especifically linear and logistic regression and boostraping. In the first image it can´t really be appreciated the line, beacuse the goal was to graph the solar curve. It shows the solar radiation (W/m2) that is capted each hour in the state of Aguascalientes. Deppending on the values of this curve and the amount of useful hours, it shows whether the solar radiation can be used to generate thermal or electric energy in the near. The equation of the line is 3.63x + 184.73 but as it was said, it isn´t quite useful but it shows a little positive tendency.

The total number of rows in this dataset is 11,000, so a boostrapping is clearly necessary because of the amount of samples.
What the second graphic shows is that the mean is 95% for sure that is bewteen 220.22 and 232.20 W/m2 per hour. The importance of this grapic is that we can have a mean of a poblation from samples without guessing its values. It´s a tool of statistical sampling, so when the experts or the gobernment want to know if it is aproppiate to install solar technology, they can consult these graphic so they know if the area is consistent with the general mean solar radiation and not just the sample mean.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235229.png" width=500> <img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235515.png" width=500>


