# Analysis of the opportunities for renewable energy in Mexico

<img src= "Pictures/Sener-renovables.jpg" width="300"> <img src= "Pictures/Captura%20de%20pantalla%202025-12-02%20193231.png" width="350"> <img src= "Pictures/Captura%20de%20pantalla%202025-12-02%20193547.png" width="300">

Currently, the overexploitation of the non-renewable resources is compelling Mexico to explore energy alternatives due to the depletion of fossil fuels and resulting global climate consequenses.

Mexico possesses significant potential in geothermal, solar, wind and hydraulic energy However, only 22% of the nation's eletricity is currently generated from renewable resources.
Consequiently, an analysis has been conducted across each Mexican state assessing its energy and economic potential, fuel consumption and comparing these facors with other countries. This efford aims to develop viable energy alternatives, using data visualizations and machine learning models.

### Data cleaning
Data cleaning was a necessary prerequisite for analysis and manipulation, as the aource databases contained inconsistencies. While common cleaning functions were applied across all documents, each CSV file was also managed individually to adress its unique requirements. 
 
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
The largest dataset utilized was the Global Energy Database, hich includes categories such as capacity and power sector emissions for various energy types (Hydro, Bioenergy, Renewables, Wind, Solar and Nuclear). With 357,014 rows and 18 columns, filtering this dataset effectively posed a significant challenge in order to extract data relevant to the desired conclusions. 
The initial scatter plot analyzed capacity versus electricity generation and focused only on the top 14 counties most relevant to Mexico. Given the disproportionate potential of the United Stated (EEUU) and China, a second scatter plot was generated to allow for a clearer visual appreciation of the differences among the remaining counties.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20234553.png" width=500> <img src="Pictures/Captura%20de%20pantalla%202025-12-04%20234616.png" width=500>

A histogram was also developed to illustrate the correlation between industrial development and energy consumption, identifying the industrial and residential sectors as Mexico´s primary energy consumers.

<img src= "Pictures/Captura%20de%20pantalla%202025-12-02%20193231.png" width="500">

The economy field is crucial, as significant capital investment is requires for large-scare energy projects. A double histogram compares the Gross Domestic Product (visualized in the graph as PIB) of each Mexican state with its total renewable energy potential. The visualization indicates that no state currently exhibits both high GDP and high renewable potential, representing a clear opportunity area for invertor and private companies. The overarching policy goals are to reduce the consumption of fossil fuels and stimulate job creation in vulnerable regions.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235603.png" width=500>

Machine Learning tools were employed, specifically linear regression, logistic regression and bootstrapping. The first visualization aimed to plot the solar curve, depicting the hourly solar radiation (W/m^2) captured in the state of Aguascalientes. Based on the curve´s values and the number of useful generation hours, it indicates the viability of using solar radiation for generating thermal or electric energy in the near future. The equation for the linear regression line is y = 3.63x + 184.73, however, as noted, the fit is not highly useful, although it suggests a slight possitive trend.

With a dataset size of 11,000 rows, bootstrapping was implemented to perform robust statistical inference. The second graphic presents the confidence interval for the mean solar radiation, indicating with 95% certainty that the true population mean lies between 220.22 and 232.20 W/m^2 per hour. The significance of this visualization is that it allows for the estimation of the population mean from a sample without assuming its value. As a statistical sampling tool, it can be consulted by experts or government entities to assess whether a specific area´s solar radiation is consistent with the general mean, thus informing the decision to install solar technology.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235229.png" width=400> <img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235515.png" width=500>

The Treemap illustrates the installed renewable energy capacity (MW) across the states of Mexico. This visualization clearly identifies the states that host the largest concentration of renewable energy generation plants and, consequently, indicates their relative contribution to Mexico´s national electricity supply.

<img src="Pictures/Captura%20de%20pantalla%202025-12-04%20235553.png" width=1000>
