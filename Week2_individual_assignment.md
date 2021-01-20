**Jupyter Notebook to go here** 
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<h1> Individual Assignment: Data Exploration"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "For this indiviudal assigment, I will run through a list of commands so I can explore my own dataset. I am unfarmiliar with each dataset below (I'm exploring two datasets), so commands like .shape, .info, or querying commands will allow me understand the size and variables associated with each dataset. In each section below, I will comment on my thought process."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<h2> Getting Started"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Geopanda Download**\n",
    "\n",
    "What this actually does, I don't quite know. Though _I do know_ this feature will allow me to import a variety of spatial data formats, and plot them on a map if all goes according to plan"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 1,
   "metadata": {},
   "outputs": [],
   "source": [
    "# import geopandas as gpd\n",
    "import geopandas as gpd"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Shoud now be able to plot map eventually"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Defining and Reading Shape File**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I'm importing my datasets."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 2,
   "metadata": {},
   "outputs": [],
   "source": [
    "# rapid_BRT = gpd.read_file('InsertHere')\n",
    "## note file location is required; identidy folders and subfolders e.g. Data/RapidBRT, File/Subfile/DocName\n",
    "rapid_BRT = gpd.read_file('Data/RapidBRT/RapidBRT1219.shp')"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 3,
   "metadata": {},
   "outputs": [],
   "source": [
    "# have not decided which data I want work with yet\n",
    "## I'm also going to take a peak at some neighborhood data\n",
    "nbhood = gpd.read_file('Data/la_county_neighorhood_v6/la_county_neighborhood_v6.shp')"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Data is now imported for the above datasets. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<h2> Getting to Know My Data"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I'm working with two shape files here. One is of rapid bus routes from LA Metro, and the other is from is LA Neigborhoods in LA and Orange Counties from the LA times. I may focus on one, but the hope is that by repeating commands with different datasets, I will become more farmiliar in manipulating shape files"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Are these gpds?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "geopandas.geodataframe.GeoDataFrame"
      ]
     },
     "execution_count": 4,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# ensuring geopanda data type\n",
    "type(rapid_BRT)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "geopandas.geodataframe.GeoDataFrame"
      ]
     },
     "execution_count": 5,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "type(nbhood)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Yes, they are gpds."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<h3> Rapid BRT Exploration"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I want some info on my rapid_BRT dataset"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'geopandas.geodataframe.GeoDataFrame'>\n",
      "RangeIndex: 87 entries, 0 to 86\n",
      "Data columns (total 5 columns):\n",
      " #   Column     Non-Null Count  Dtype   \n",
      "---  ------     --------------  -----   \n",
      " 0   VAR_ROUTE  87 non-null     object  \n",
      " 1   VAR_IDENT  87 non-null     object  \n",
      " 2   VAR_DIREC  87 non-null     int64   \n",
      " 3   VAR_DESCR  85 non-null     object  \n",
      " 4   geometry   87 non-null     geometry\n",
      "dtypes: geometry(1), int64(1), object(3)\n",
      "memory usage: 3.5+ KB\n"
     ]
    }
   ],
   "source": [
    "# overview of my rapid_BRT data\n",
    "rapid_BRT.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Above is detailing what's in my data. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Looking at my datatypes, should be similar to above."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 7,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "VAR_ROUTE      object\n",
       "VAR_IDENT      object\n",
       "VAR_DIREC       int64\n",
       "VAR_DESCR      object\n",
       "geometry     geometry\n",
       "dtype: object"
      ]
     },
     "execution_count": 7,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# want to take a look at dyptes though I don't expect to see any new information\n",
    "rapid_BRT.dtypes"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Note here, that gpds describe datatypes differently than pd or in python"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I'm checking the shape of my data."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 8,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(87, 5)"
      ]
     },
     "execution_count": 8,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# how many rows and columns am I working with?\n",
    "rapid_BRT.shape"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I can see there are 87 rows and 5 columns. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking my columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 9,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "['VAR_ROUTE', 'VAR_IDENT', 'VAR_DIREC', 'VAR_DESCR', 'geometry']"
      ]
     },
     "execution_count": 9,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# what are my columns? \n",
    "rapid_BRT.columns.to_list()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The above lists my columns. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "What does the first 5 rows of my data look like?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 10,
   "metadata": {
    "scrolled": false
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>VAR_DIREC</th>\n",
       "      <th>VAR_DESCR</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>2</td>\n",
       "      <td>END TO END - RAPID - TO DIV13O</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>2</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>2</td>\n",
       "      <td>TRIPS START SEPSAN</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END- RAPID - FROM DIV13O</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>3</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  VAR_ROUTE VAR_IDENT  VAR_DIREC                        VAR_DESCR  \\\n",
       "0       704        E1          2   END TO END - RAPID - TO DIV13O   \n",
       "1       704        E3          2                 NEBSEP Shortline   \n",
       "2       704        E6          2               TRIPS START SEPSAN   \n",
       "3       704        W1          3  END TO END- RAPID - FROM DIV13O   \n",
       "4       704        W3          3                 NEBSEP Shortline   \n",
       "\n",
       "                                            geometry  \n",
       "0  LINESTRING (-118.49997 34.01574, -118.50054 34...  \n",
       "1  LINESTRING (-118.44327 34.04567, -118.44335 34...  \n",
       "2  LINESTRING (-118.44356 34.04791, -118.44354 34...  \n",
       "3  LINESTRING (-118.23190 34.05663, -118.23230 34...  \n",
       "4  LINESTRING (-118.38430 34.08485, -118.38471 34...  "
      ]
     },
     "execution_count": 10,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# quick preview of my data\n",
    "rapid_BRT.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Above shows the first 5 rows of data. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "What does the last 5 rows of my data look like?"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 11,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>VAR_DIREC</th>\n",
       "      <th>VAR_DESCR</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>901</td>\n",
       "      <td>E2</td>\n",
       "      <td>2</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.59682 34.19051, -118.59747 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>83</th>\n",
       "      <td>901</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.37799 34.16852, -118.37744 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>901</td>\n",
       "      <td>W2</td>\n",
       "      <td>3</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.57169 34.18742, -118.57207 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>0</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>86</th>\n",
       "      <td>910</td>\n",
       "      <td>S1</td>\n",
       "      <td>1</td>\n",
       "      <td>None</td>\n",
       "      <td>LINESTRING (-118.04513 34.07202, -118.04598 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT  VAR_DIREC               VAR_DESCR  \\\n",
       "82       901        E2          2  CANOGA STATION LAYOVER   \n",
       "83       901        W1          3              END TO END   \n",
       "84       901        W2          3  CANOGA STATION LAYOVER   \n",
       "85       910        N1          0              END TO END   \n",
       "86       910        S1          1                    None   \n",
       "\n",
       "                                             geometry  \n",
       "82  LINESTRING (-118.59682 34.19051, -118.59747 34...  \n",
       "83  LINESTRING (-118.37799 34.16852, -118.37744 34...  \n",
       "84  LINESTRING (-118.57169 34.18742, -118.57207 34...  \n",
       "85  LINESTRING (-118.28798 33.72493, -118.28798 33...  \n",
       "86  LINESTRING (-118.04513 34.07202, -118.04598 34...  "
      ]
     },
     "execution_count": 11,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# preview of tail\n",
    "rapid_BRT.tail()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Above shows the last 5 rows of my data."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Intial take of what these columns mean, plus I get to work on some more Markdown skills:\n",
    "\n",
    "Column Title | What It Means?\n",
    "----------------- |----------------\n",
    "VAR_ROUTE | Bus Route\n",
    "VAR_IDENT | Direction/Number; unsure?\n",
    "VAR_DIREC | Unsure\n",
    "VAR_DESCR | Route Description\n",
    "geometery | Geometry"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Reminding myself of my columns"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 16,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "Index(['VAR_ROUTE', 'VAR_IDENT', 'VAR_DIREC', 'VAR_DESCR', 'geometry'], dtype='object')"
      ]
     },
     "execution_count": 16,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# I know my columns, but let's repeat the action here. May try and rename columns in further sequencing\n",
    "rapid_BRT.columns"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Ah, those are my columns."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I am creating a variable which I may manipulate later."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [],
   "source": [
    "# going to create a variable for my bus routes\n",
    "BRT_count = rapid_BRT['VAR_ROUTE'].value_counts()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Now I'm checking to see if the above variable works with the below command."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "720    10\n",
       "745     7\n",
       "704     6\n",
       "744     5\n",
       "728     5\n",
       "762     4\n",
       "780     4\n",
       "901     4\n",
       "705     4\n",
       "733     4\n",
       "754     4\n",
       "734     4\n",
       "760     4\n",
       "710     3\n",
       "750     3\n",
       "770     3\n",
       "740     3\n",
       "794     2\n",
       "910     2\n",
       "757     2\n",
       "788     2\n",
       "751     2\n",
       "Name: VAR_ROUTE, dtype: int64"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#ensuring BRT_count works\n",
    "BRT_count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The above command worked! BRT_count is a new variable that I have defined."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Note to self, follow up to check-in on problems with reset.index() command and renaming convention**\n",
    "\n",
    "1. #converting the series to a df; BRT_count = BRT_count.reset.index()\n",
    "1. #working on this reset.index() command;bus_count = bus_count.reset.index()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking to see the values in my column. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 17,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0     704\n",
       "1     704\n",
       "2     704\n",
       "3     704\n",
       "4     704\n",
       "     ... \n",
       "82    901\n",
       "83    901\n",
       "84    901\n",
       "85    910\n",
       "86    910\n",
       "Name: VAR_ROUTE, Length: 87, dtype: object"
      ]
     },
     "execution_count": 17,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# scoping values in VAR_ROUTE Column\n",
    "rapid_BRT['VAR_ROUTE']"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The above shows the beginning and end of one column. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Using another method to see the tail ends of a specific column."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 18,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0     704\n",
       "1     704\n",
       "2     704\n",
       "3     704\n",
       "4     704\n",
       "     ... \n",
       "82    901\n",
       "83    901\n",
       "84    901\n",
       "85    910\n",
       "86    910\n",
       "Name: VAR_ROUTE, Length: 87, dtype: object"
      ]
     },
     "execution_count": 18,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# another way to scope out column\n",
    "## prefer this method; looks cleaner\n",
    "rapid_BRT.VAR_ROUTE"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The output shows the tail ends of my a designated column."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Combined two commands to see the head of one variable."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 19,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0    704\n",
       "1    704\n",
       "2    704\n",
       "3    704\n",
       "4    704\n",
       "Name: VAR_ROUTE, dtype: object"
      ]
     },
     "execution_count": 19,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# playing around with combining different commands\n",
    "rapid_BRT.VAR_ROUTE.head()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The output shows the first five values for the a single column."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking to see the frequency of each variable in one column."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 20,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "720    10\n",
       "745     7\n",
       "704     6\n",
       "728     5\n",
       "744     5\n",
       "733     4\n",
       "705     4\n",
       "762     4\n",
       "734     4\n",
       "780     4\n",
       "754     4\n",
       "901     4\n",
       "760     4\n",
       "750     3\n",
       "770     3\n",
       "710     3\n",
       "740     3\n",
       "794     2\n",
       "788     2\n",
       "751     2\n",
       "757     2\n",
       "910     2\n",
       "Name: VAR_ROUTE, dtype: int64"
      ]
     },
     "execution_count": 20,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# how many VAR_ROUTE variables are there in this column?\n",
    "rapid_BRT['VAR_ROUTE'].value_counts()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The output shows the how many times each bus route comes up in VAR_ROUTE. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Going to define the above column as a variable to save on time if I want to access it later."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 21,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "720    10\n",
       "745     7\n",
       "704     6\n",
       "728     5\n",
       "744     5\n",
       "733     4\n",
       "705     4\n",
       "762     4\n",
       "734     4\n",
       "780     4\n",
       "754     4\n",
       "901     4\n",
       "760     4\n",
       "750     3\n",
       "770     3\n",
       "710     3\n",
       "740     3\n",
       "794     2\n",
       "788     2\n",
       "751     2\n",
       "757     2\n",
       "910     2\n",
       "Name: VAR_ROUTE, dtype: int64"
      ]
     },
     "execution_count": 21,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# saving bus route as a variable \n",
    "bus_count = rapid_BRT['VAR_ROUTE'].value_counts()\n",
    "bus_count"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I now have a new variable that's defined. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking to see the type of my new variable. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 22,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "pandas.core.series.Series"
      ]
     },
     "execution_count": 22,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# checking the type\n",
    "type(bus_count)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This variable is a pd. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking the tails of another column."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "0     E1\n",
       "1     E3\n",
       "2     E6\n",
       "3     W1\n",
       "4     W3\n",
       "      ..\n",
       "82    E2\n",
       "83    W1\n",
       "84    W2\n",
       "85    N1\n",
       "86    S1\n",
       "Name: VAR_IDENT, Length: 87, dtype: object"
      ]
     },
     "execution_count": 25,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# curious to the variables in VAR_IDENT\n",
    "rapid_BRT.VAR_IDENT"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Output shows the tail ends of VAR_IDENT."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I want to see the frequency of each VAR_IDENT variable."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "N1    17\n",
       "S1    13\n",
       "E1    13\n",
       "W1     9\n",
       "W2     5\n",
       "E2     5\n",
       "N2     5\n",
       "S2     3\n",
       "W3     3\n",
       "E3     3\n",
       "N3     2\n",
       "EB     1\n",
       "SP     1\n",
       "E7     1\n",
       "E4     1\n",
       "E5     1\n",
       "E6     1\n",
       "W5     1\n",
       "N4     1\n",
       "NP     1\n",
       "Name: VAR_IDENT, dtype: int64"
      ]
     },
     "execution_count": 25,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# I want to see the value counts for VAR_IDENT\n",
    "rapid_BRT['VAR_IDENT'].value_counts()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The above shows how many times each variable comes up in this particular column."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Filtering the data**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Checking the info on my data again."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'geopandas.geodataframe.GeoDataFrame'>\n",
      "RangeIndex: 87 entries, 0 to 86\n",
      "Data columns (total 5 columns):\n",
      " #   Column     Non-Null Count  Dtype   \n",
      "---  ------     --------------  -----   \n",
      " 0   VAR_ROUTE  87 non-null     object  \n",
      " 1   VAR_IDENT  87 non-null     object  \n",
      " 2   VAR_DIREC  87 non-null     int64   \n",
      " 3   VAR_DESCR  85 non-null     object  \n",
      " 4   geometry   87 non-null     geometry\n",
      "dtypes: geometry(1), int64(1), object(3)\n",
      "memory usage: 3.5+ KB\n"
     ]
    }
   ],
   "source": [
    "#what am i working with again? \n",
    "rapid_BRT.info()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Again, the above details what's in my data. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I don't know what I want to trim yet, so I'm going to take a look at my data again."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 27,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>VAR_DIREC</th>\n",
       "      <th>VAR_DESCR</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>2</td>\n",
       "      <td>END TO END - RAPID - TO DIV13O</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>2</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>2</td>\n",
       "      <td>TRIPS START SEPSAN</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END- RAPID - FROM DIV13O</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>3</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>901</td>\n",
       "      <td>E2</td>\n",
       "      <td>2</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.59682 34.19051, -118.59747 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>83</th>\n",
       "      <td>901</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.37799 34.16852, -118.37744 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>901</td>\n",
       "      <td>W2</td>\n",
       "      <td>3</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.57169 34.18742, -118.57207 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>0</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>86</th>\n",
       "      <td>910</td>\n",
       "      <td>S1</td>\n",
       "      <td>1</td>\n",
       "      <td>None</td>\n",
       "      <td>LINESTRING (-118.04513 34.07202, -118.04598 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>87 rows × 5 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT  VAR_DIREC                        VAR_DESCR  \\\n",
       "0        704        E1          2   END TO END - RAPID - TO DIV13O   \n",
       "1        704        E3          2                 NEBSEP Shortline   \n",
       "2        704        E6          2               TRIPS START SEPSAN   \n",
       "3        704        W1          3  END TO END- RAPID - FROM DIV13O   \n",
       "4        704        W3          3                 NEBSEP Shortline   \n",
       "..       ...       ...        ...                              ...   \n",
       "82       901        E2          2           CANOGA STATION LAYOVER   \n",
       "83       901        W1          3                       END TO END   \n",
       "84       901        W2          3           CANOGA STATION LAYOVER   \n",
       "85       910        N1          0                       END TO END   \n",
       "86       910        S1          1                             None   \n",
       "\n",
       "                                             geometry  \n",
       "0   LINESTRING (-118.49997 34.01574, -118.50054 34...  \n",
       "1   LINESTRING (-118.44327 34.04567, -118.44335 34...  \n",
       "2   LINESTRING (-118.44356 34.04791, -118.44354 34...  \n",
       "3   LINESTRING (-118.23190 34.05663, -118.23230 34...  \n",
       "4   LINESTRING (-118.38430 34.08485, -118.38471 34...  \n",
       "..                                                ...  \n",
       "82  LINESTRING (-118.59682 34.19051, -118.59747 34...  \n",
       "83  LINESTRING (-118.37799 34.16852, -118.37744 34...  \n",
       "84  LINESTRING (-118.57169 34.18742, -118.57207 34...  \n",
       "85  LINESTRING (-118.28798 33.72493, -118.28798 33...  \n",
       "86  LINESTRING (-118.04513 34.07202, -118.04598 34...  \n",
       "\n",
       "[87 rows x 5 columns]"
      ]
     },
     "execution_count": 27,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rapid_BRT"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Output shows tail ends of my data. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "*I'm unsure how the above and below commands differ. Reminder to look at this again.*"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I am feeding a df a list of column names."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 28,
   "metadata": {
    "scrolled": false
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>VAR_DIREC</th>\n",
       "      <th>VAR_DESCR</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>2</td>\n",
       "      <td>END TO END - RAPID - TO DIV13O</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>2</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>2</td>\n",
       "      <td>TRIPS START SEPSAN</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END- RAPID - FROM DIV13O</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>3</td>\n",
       "      <td>NEBSEP Shortline</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>901</td>\n",
       "      <td>E2</td>\n",
       "      <td>2</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.59682 34.19051, -118.59747 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>83</th>\n",
       "      <td>901</td>\n",
       "      <td>W1</td>\n",
       "      <td>3</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.37799 34.16852, -118.37744 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>901</td>\n",
       "      <td>W2</td>\n",
       "      <td>3</td>\n",
       "      <td>CANOGA STATION LAYOVER</td>\n",
       "      <td>LINESTRING (-118.57169 34.18742, -118.57207 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>0</td>\n",
       "      <td>END TO END</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>86</th>\n",
       "      <td>910</td>\n",
       "      <td>S1</td>\n",
       "      <td>1</td>\n",
       "      <td>None</td>\n",
       "      <td>LINESTRING (-118.04513 34.07202, -118.04598 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>87 rows × 5 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT  VAR_DIREC                        VAR_DESCR  \\\n",
       "0        704        E1          2   END TO END - RAPID - TO DIV13O   \n",
       "1        704        E3          2                 NEBSEP Shortline   \n",
       "2        704        E6          2               TRIPS START SEPSAN   \n",
       "3        704        W1          3  END TO END- RAPID - FROM DIV13O   \n",
       "4        704        W3          3                 NEBSEP Shortline   \n",
       "..       ...       ...        ...                              ...   \n",
       "82       901        E2          2           CANOGA STATION LAYOVER   \n",
       "83       901        W1          3                       END TO END   \n",
       "84       901        W2          3           CANOGA STATION LAYOVER   \n",
       "85       910        N1          0                       END TO END   \n",
       "86       910        S1          1                             None   \n",
       "\n",
       "                                             geometry  \n",
       "0   LINESTRING (-118.49997 34.01574, -118.50054 34...  \n",
       "1   LINESTRING (-118.44327 34.04567, -118.44335 34...  \n",
       "2   LINESTRING (-118.44356 34.04791, -118.44354 34...  \n",
       "3   LINESTRING (-118.23190 34.05663, -118.23230 34...  \n",
       "4   LINESTRING (-118.38430 34.08485, -118.38471 34...  \n",
       "..                                                ...  \n",
       "82  LINESTRING (-118.59682 34.19051, -118.59747 34...  \n",
       "83  LINESTRING (-118.37799 34.16852, -118.37744 34...  \n",
       "84  LINESTRING (-118.57169 34.18742, -118.57207 34...  \n",
       "85  LINESTRING (-118.28798 33.72493, -118.28798 33...  \n",
       "86  LINESTRING (-118.04513 34.07202, -118.04598 34...  \n",
       "\n",
       "[87 rows x 5 columns]"
      ]
     },
     "execution_count": 28,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# dataframe \n",
    "## Apparently, I am feeding the list the dataframe a list of column names\n",
    "rapid_BRT[['VAR_ROUTE', 'VAR_IDENT', 'VAR_DIREC', 'VAR_DESCR', 'geometry']]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "What I think I was supposed to do feed the df a particular set of columns, not just all of them, but at least I know that now...."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Going to select the columns/stuff I want from the above table"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 29,
   "metadata": {},
   "outputs": [],
   "source": [
    "stuff_i_want = ['VAR_ROUTE', 'VAR_IDENT', 'geometry']"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Variable created that corresponds to certain columns"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Going to run my new variable and see what happens."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 30,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "['VAR_ROUTE', 'VAR_IDENT', 'geometry']"
      ]
     },
     "execution_count": 30,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# what happens when I execute stuff_i_want? will i get the table?\n",
    "stuff_i_want"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "New variable shows its associated columns."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Will now produce a table from my new variable."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 31,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>901</td>\n",
       "      <td>E2</td>\n",
       "      <td>LINESTRING (-118.59682 34.19051, -118.59747 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>83</th>\n",
       "      <td>901</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.37799 34.16852, -118.37744 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>901</td>\n",
       "      <td>W2</td>\n",
       "      <td>LINESTRING (-118.57169 34.18742, -118.57207 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>86</th>\n",
       "      <td>910</td>\n",
       "      <td>S1</td>\n",
       "      <td>LINESTRING (-118.04513 34.07202, -118.04598 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>87 rows × 3 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT                                           geometry\n",
       "0        704        E1  LINESTRING (-118.49997 34.01574, -118.50054 34...\n",
       "1        704        E3  LINESTRING (-118.44327 34.04567, -118.44335 34...\n",
       "2        704        E6  LINESTRING (-118.44356 34.04791, -118.44354 34...\n",
       "3        704        W1  LINESTRING (-118.23190 34.05663, -118.23230 34...\n",
       "4        704        W3  LINESTRING (-118.38430 34.08485, -118.38471 34...\n",
       "..       ...       ...                                                ...\n",
       "82       901        E2  LINESTRING (-118.59682 34.19051, -118.59747 34...\n",
       "83       901        W1  LINESTRING (-118.37799 34.16852, -118.37744 34...\n",
       "84       901        W2  LINESTRING (-118.57169 34.18742, -118.57207 34...\n",
       "85       910        N1  LINESTRING (-118.28798 33.72493, -118.28798 33...\n",
       "86       910        S1  LINESTRING (-118.04513 34.07202, -118.04598 34...\n",
       "\n",
       "[87 rows x 3 columns]"
      ]
     },
     "execution_count": 31,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# did not get the table, i need to apply stuff_i_want to rapid_BRT with brackets\n",
    "rapid_BRT[stuff_i_want]"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "New table for my new variable that lists only certain columns. "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "\n",
    "I'm going to define my trimmed dataset, will also copy my data as good practice\n",
    "\n",
    "\n"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>...</th>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "      <td>...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>82</th>\n",
       "      <td>901</td>\n",
       "      <td>E2</td>\n",
       "      <td>LINESTRING (-118.59682 34.19051, -118.59747 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>83</th>\n",
       "      <td>901</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.37799 34.16852, -118.37744 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>84</th>\n",
       "      <td>901</td>\n",
       "      <td>W2</td>\n",
       "      <td>LINESTRING (-118.57169 34.18742, -118.57207 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>86</th>\n",
       "      <td>910</td>\n",
       "      <td>S1</td>\n",
       "      <td>LINESTRING (-118.04513 34.07202, -118.04598 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "<p>87 rows × 3 columns</p>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT                                           geometry\n",
       "0        704        E1  LINESTRING (-118.49997 34.01574, -118.50054 34...\n",
       "1        704        E3  LINESTRING (-118.44327 34.04567, -118.44335 34...\n",
       "2        704        E6  LINESTRING (-118.44356 34.04791, -118.44354 34...\n",
       "3        704        W1  LINESTRING (-118.23190 34.05663, -118.23230 34...\n",
       "4        704        W3  LINESTRING (-118.38430 34.08485, -118.38471 34...\n",
       "..       ...       ...                                                ...\n",
       "82       901        E2  LINESTRING (-118.59682 34.19051, -118.59747 34...\n",
       "83       901        W1  LINESTRING (-118.37799 34.16852, -118.37744 34...\n",
       "84       901        W2  LINESTRING (-118.57169 34.18742, -118.57207 34...\n",
       "85       910        N1  LINESTRING (-118.28798 33.72493, -118.28798 33...\n",
       "86       910        S1  LINESTRING (-118.04513 34.07202, -118.04598 34...\n",
       "\n",
       "[87 rows x 3 columns]"
      ]
     },
     "execution_count": 32,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rapid_BRT_trimmed = rapid_BRT[stuff_i_want].copy()\n",
    "rapid_BRT_trimmed"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I now have a new variable that was created from another variable I created"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I want to experiment with other filtering methods"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  VAR_ROUTE VAR_IDENT                                           geometry\n",
       "0       704        E1  LINESTRING (-118.49997 34.01574, -118.50054 34...\n",
       "1       704        E3  LINESTRING (-118.44327 34.04567, -118.44335 34...\n",
       "2       704        E6  LINESTRING (-118.44356 34.04791, -118.44354 34...\n",
       "3       704        W1  LINESTRING (-118.23190 34.05663, -118.23230 34...\n",
       "4       704        W3  LINESTRING (-118.38430 34.08485, -118.38471 34...\n",
       "5       704        E1  LINESTRING (-118.23190 34.05663, -118.23230 34..."
      ]
     },
     "execution_count": 33,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# slimmed, clean query\n",
    "## future me: watch the syntaxt, aka quote use\n",
    "rapid_BRT_trimmed.query(\"VAR_ROUTE == '704'\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The output shows each row with the 704 value."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "More trimming using loc."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 34,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.49997 34.01574, -118.50054 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>704</td>\n",
       "      <td>E3</td>\n",
       "      <td>LINESTRING (-118.44327 34.04567, -118.44335 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>704</td>\n",
       "      <td>E6</td>\n",
       "      <td>LINESTRING (-118.44356 34.04791, -118.44354 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>704</td>\n",
       "      <td>W1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>704</td>\n",
       "      <td>W3</td>\n",
       "      <td>LINESTRING (-118.38430 34.08485, -118.38471 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>5</th>\n",
       "      <td>704</td>\n",
       "      <td>E1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23230 34...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "  VAR_ROUTE VAR_IDENT                                           geometry\n",
       "0       704        E1  LINESTRING (-118.49997 34.01574, -118.50054 34...\n",
       "1       704        E3  LINESTRING (-118.44327 34.04567, -118.44335 34...\n",
       "2       704        E6  LINESTRING (-118.44356 34.04791, -118.44354 34...\n",
       "3       704        W1  LINESTRING (-118.23190 34.05663, -118.23230 34...\n",
       "4       704        W3  LINESTRING (-118.38430 34.08485, -118.38471 34...\n",
       "5       704        E1  LINESTRING (-118.23190 34.05663, -118.23230 34..."
      ]
     },
     "execution_count": 34,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#loc methodology\n",
    "rapid_BRT_trimmed.loc[rapid_BRT_trimmed['VAR_ROUTE'] == '704']"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "This was one was trickier with syntaxt, but can offer robust opportunities. But the slicing remains the same as above."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Will try a cleaner syntaxt with query to detail VAR_IDENT."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 35,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>VAR_ROUTE</th>\n",
       "      <th>VAR_IDENT</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>6</th>\n",
       "      <td>705</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.22745 34.00463, -118.22754 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>10</th>\n",
       "      <td>710</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.35698 33.87176, -118.35696 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>32</th>\n",
       "      <td>734</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.43460 34.03512, -118.43536 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>36</th>\n",
       "      <td>740</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.35460 33.86554, -118.35483 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>44</th>\n",
       "      <td>745</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.28186 33.92774, -118.28191 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>49</th>\n",
       "      <td>745</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.23190 34.05663, -118.23209 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>50</th>\n",
       "      <td>745</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.23209 34.05622, -118.23230 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>54</th>\n",
       "      <td>751</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.22304 33.96346, -118.22298 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>56</th>\n",
       "      <td>754</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.29150 33.92401, -118.29149 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>60</th>\n",
       "      <td>757</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.32649 33.92536, -118.32649 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>62</th>\n",
       "      <td>760</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.20988 33.92443, -118.20991 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>66</th>\n",
       "      <td>762</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.18452 33.95729, -118.18489 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>68</th>\n",
       "      <td>762</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.22290 33.87596, -118.22297 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>69</th>\n",
       "      <td>762</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.18312 33.95191, -118.18323 33...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>77</th>\n",
       "      <td>788</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.43460 34.03512, -118.43536 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>79</th>\n",
       "      <td>794</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.26461 34.03322, -118.26431 34...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>85</th>\n",
       "      <td>910</td>\n",
       "      <td>N1</td>\n",
       "      <td>LINESTRING (-118.28798 33.72493, -118.28798 33...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "   VAR_ROUTE VAR_IDENT                                           geometry\n",
       "6        705        N1  LINESTRING (-118.22745 34.00463, -118.22754 34...\n",
       "10       710        N1  LINESTRING (-118.35698 33.87176, -118.35696 33...\n",
       "32       734        N1  LINESTRING (-118.43460 34.03512, -118.43536 34...\n",
       "36       740        N1  LINESTRING (-118.35460 33.86554, -118.35483 33...\n",
       "44       745        N1  LINESTRING (-118.28186 33.92774, -118.28191 33...\n",
       "49       745        N1  LINESTRING (-118.23190 34.05663, -118.23209 34...\n",
       "50       745        N1  LINESTRING (-118.23209 34.05622, -118.23230 34...\n",
       "54       751        N1  LINESTRING (-118.22304 33.96346, -118.22298 33...\n",
       "56       754        N1  LINESTRING (-118.29150 33.92401, -118.29149 33...\n",
       "60       757        N1  LINESTRING (-118.32649 33.92536, -118.32649 33...\n",
       "62       760        N1  LINESTRING (-118.20988 33.92443, -118.20991 33...\n",
       "66       762        N1  LINESTRING (-118.18452 33.95729, -118.18489 33...\n",
       "68       762        N1  LINESTRING (-118.22290 33.87596, -118.22297 33...\n",
       "69       762        N1  LINESTRING (-118.18312 33.95191, -118.18323 33...\n",
       "77       788        N1  LINESTRING (-118.43460 34.03512, -118.43536 34...\n",
       "79       794        N1  LINESTRING (-118.26461 34.03322, -118.26431 34...\n",
       "85       910        N1  LINESTRING (-118.28798 33.72493, -118.28798 33..."
      ]
     },
     "execution_count": 35,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "rapid_BRT_trimmed.query(\"VAR_IDENT == 'N1'\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Output shows N1 rows for VAR_IDENT."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**Will try some plotting now**"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "I am plotting and have no idea what will happen."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 36,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f64474a5fa0>"
      ]
     },
     "execution_count": 36,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "#curious what will happen with the basic plot command if little information if given\n",
    "rapid_BRT.plot()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "WOW, that is so cool. I forgot about the spatial component of this dataset. So this plot used the geometry points to map the bus routes."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 37,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f6445c09700>"
      ]
     },
     "execution_count": 37,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# also curious to what the trimmed dataset will look like, I expect the same as above. It has the same geometric points\n",
    "rapid_BRT_trimmed.plot()"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Will add some color to my routes."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 38,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f6443b6f070>"
      ]
     },
     "execution_count": 38,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 1440x864 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "# I don'd understand the syntaxt of this command yet, but looked at the WK 2 class notebook and wanted to change the colors of the bus lines\n",
    "rapid_BRT.plot(\n",
    "            figsize=(20,12),   #size of the plot (a bit bigger than the default)\n",
    "            column = 'VAR_ROUTE',   # column that defines the color of the dots\n",
    "            legend = True,     # add a legend           \n",
    "            legend_kwds={\n",
    "               'loc': 'upper right',\n",
    "               'bbox_to_anchor':(1.3,1)\n",
    "            }                  # this puts the legend to the side\n",
    ") "
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Bus routes now have different colors (more or less), and there's a legend as well."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "<h3>Nbhood Data's Turn Now"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "**The below data exploration is just for fun on my end. No need to look at it. It's a repeat of the above essentially, but with different data.**"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 39,
   "metadata": {
    "scrolled": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'geopandas.geodataframe.GeoDataFrame'>\n",
      "RangeIndex: 318 entries, 0 to 317\n",
      "Data columns (total 13 columns):\n",
      " #   Column      Non-Null Count  Dtype   \n",
      "---  ------      --------------  -----   \n",
      " 0   slug        318 non-null    object  \n",
      " 1   set         318 non-null    object  \n",
      " 2   kind        318 non-null    object  \n",
      " 3   external_i  318 non-null    object  \n",
      " 4   name        318 non-null    object  \n",
      " 5   display_na  318 non-null    object  \n",
      " 6   city        114 non-null    object  \n",
      " 7   name_1      0 non-null      object  \n",
      " 8   region      318 non-null    object  \n",
      " 9   county      318 non-null    object  \n",
      " 10  type        318 non-null    object  \n",
      " 11  slug_1      0 non-null      object  \n",
      " 12  geometry    318 non-null    geometry\n",
      "dtypes: geometry(1), object(12)\n",
      "memory usage: 32.4+ KB\n"
     ]
    }
   ],
   "source": [
    "#survey of nbhood data\n",
    "nbhood.info()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 40,
   "metadata": {
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "slug            object\n",
       "set             object\n",
       "kind            object\n",
       "external_i      object\n",
       "name            object\n",
       "display_na      object\n",
       "city            object\n",
       "name_1          object\n",
       "region          object\n",
       "county          object\n",
       "type            object\n",
       "slug_1          object\n",
       "geometry      geometry\n",
       "dtype: object"
      ]
     },
     "execution_count": 40,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# prefer info over dytype, but want to look at dtypes\n",
    "nbhood.dtypes"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 41,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "(318, 13)"
      ]
     },
     "execution_count": 41,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#checking rows and columns\n",
    "nbhood.shape"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 42,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "['slug',\n",
       " 'set',\n",
       " 'kind',\n",
       " 'external_i',\n",
       " 'name',\n",
       " 'display_na',\n",
       " 'city',\n",
       " 'name_1',\n",
       " 'region',\n",
       " 'county',\n",
       " 'type',\n",
       " 'slug_1',\n",
       " 'geometry']"
      ]
     },
     "execution_count": 42,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# checking columns\n",
    "nbhood.columns.to_list()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 44,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/html": [
       "<div>\n",
       "<style scoped>\n",
       "    .dataframe tbody tr th:only-of-type {\n",
       "        vertical-align: middle;\n",
       "    }\n",
       "\n",
       "    .dataframe tbody tr th {\n",
       "        vertical-align: top;\n",
       "    }\n",
       "\n",
       "    .dataframe thead th {\n",
       "        text-align: right;\n",
       "    }\n",
       "</style>\n",
       "<table border=\"1\" class=\"dataframe\">\n",
       "  <thead>\n",
       "    <tr style=\"text-align: right;\">\n",
       "      <th></th>\n",
       "      <th>slug</th>\n",
       "      <th>set</th>\n",
       "      <th>kind</th>\n",
       "      <th>external_i</th>\n",
       "      <th>name</th>\n",
       "      <th>display_na</th>\n",
       "      <th>city</th>\n",
       "      <th>name_1</th>\n",
       "      <th>region</th>\n",
       "      <th>county</th>\n",
       "      <th>type</th>\n",
       "      <th>slug_1</th>\n",
       "      <th>geometry</th>\n",
       "    </tr>\n",
       "  </thead>\n",
       "  <tbody>\n",
       "    <tr>\n",
       "      <th>0</th>\n",
       "      <td>acton</td>\n",
       "      <td>L.A. County Neighborhoods (V6)</td>\n",
       "      <td>L.A. County Neighborhood (V6)</td>\n",
       "      <td>acton</td>\n",
       "      <td>Acton</td>\n",
       "      <td>Acton L.A. County Neighborhood (V6)</td>\n",
       "      <td>None</td>\n",
       "      <td>None</td>\n",
       "      <td>antelope-valley</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>unincorporated-area</td>\n",
       "      <td>None</td>\n",
       "      <td>POLYGON ((-118.20703 34.53902, -118.18941 34.5...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>1</th>\n",
       "      <td>adams-normandie</td>\n",
       "      <td>L.A. County Neighborhoods (V6)</td>\n",
       "      <td>L.A. County Neighborhood (V6)</td>\n",
       "      <td>adams-normandie</td>\n",
       "      <td>Adams-Normandie</td>\n",
       "      <td>Adams-Normandie L.A. County Neighborhood (V6)</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>None</td>\n",
       "      <td>south-la</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>segment-of-a-city</td>\n",
       "      <td>None</td>\n",
       "      <td>POLYGON ((-118.30800 34.03740, -118.30067 34.0...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>2</th>\n",
       "      <td>agoura-hills</td>\n",
       "      <td>L.A. County Neighborhoods (V6)</td>\n",
       "      <td>L.A. County Neighborhood (V6)</td>\n",
       "      <td>agoura-hills</td>\n",
       "      <td>Agoura Hills</td>\n",
       "      <td>Agoura Hills L.A. County Neighborhood (V6)</td>\n",
       "      <td>None</td>\n",
       "      <td>None</td>\n",
       "      <td>santa-monica-mountains</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>standalone-city</td>\n",
       "      <td>None</td>\n",
       "      <td>POLYGON ((-118.77621 34.16816, -118.72632 34.1...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>3</th>\n",
       "      <td>agua-dulce</td>\n",
       "      <td>L.A. County Neighborhoods (V6)</td>\n",
       "      <td>L.A. County Neighborhood (V6)</td>\n",
       "      <td>agua-dulce</td>\n",
       "      <td>Agua Dulce</td>\n",
       "      <td>Agua Dulce L.A. County Neighborhood (V6)</td>\n",
       "      <td>None</td>\n",
       "      <td>None</td>\n",
       "      <td>northwest-county</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>unincorporated-area</td>\n",
       "      <td>None</td>\n",
       "      <td>MULTIPOLYGON (((-118.37822 34.48811, -118.3783...</td>\n",
       "    </tr>\n",
       "    <tr>\n",
       "      <th>4</th>\n",
       "      <td>alhambra</td>\n",
       "      <td>L.A. County Neighborhoods (V6)</td>\n",
       "      <td>L.A. County Neighborhood (V6)</td>\n",
       "      <td>alhambra</td>\n",
       "      <td>Alhambra</td>\n",
       "      <td>Alhambra L.A. County Neighborhood (V6)</td>\n",
       "      <td>None</td>\n",
       "      <td>None</td>\n",
       "      <td>san-gabriel-valley</td>\n",
       "      <td>los-angeles</td>\n",
       "      <td>standalone-city</td>\n",
       "      <td>None</td>\n",
       "      <td>POLYGON ((-118.12175 34.10504, -118.11687 34.1...</td>\n",
       "    </tr>\n",
       "  </tbody>\n",
       "</table>\n",
       "</div>"
      ],
      "text/plain": [
       "              slug                             set  \\\n",
       "0            acton  L.A. County Neighborhoods (V6)   \n",
       "1  adams-normandie  L.A. County Neighborhoods (V6)   \n",
       "2     agoura-hills  L.A. County Neighborhoods (V6)   \n",
       "3       agua-dulce  L.A. County Neighborhoods (V6)   \n",
       "4         alhambra  L.A. County Neighborhoods (V6)   \n",
       "\n",
       "                            kind       external_i             name  \\\n",
       "0  L.A. County Neighborhood (V6)            acton            Acton   \n",
       "1  L.A. County Neighborhood (V6)  adams-normandie  Adams-Normandie   \n",
       "2  L.A. County Neighborhood (V6)     agoura-hills     Agoura Hills   \n",
       "3  L.A. County Neighborhood (V6)       agua-dulce       Agua Dulce   \n",
       "4  L.A. County Neighborhood (V6)         alhambra         Alhambra   \n",
       "\n",
       "                                      display_na         city name_1  \\\n",
       "0            Acton L.A. County Neighborhood (V6)         None   None   \n",
       "1  Adams-Normandie L.A. County Neighborhood (V6)  los-angeles   None   \n",
       "2     Agoura Hills L.A. County Neighborhood (V6)         None   None   \n",
       "3       Agua Dulce L.A. County Neighborhood (V6)         None   None   \n",
       "4         Alhambra L.A. County Neighborhood (V6)         None   None   \n",
       "\n",
       "                   region       county                 type slug_1  \\\n",
       "0         antelope-valley  los-angeles  unincorporated-area   None   \n",
       "1                south-la  los-angeles    segment-of-a-city   None   \n",
       "2  santa-monica-mountains  los-angeles      standalone-city   None   \n",
       "3        northwest-county  los-angeles  unincorporated-area   None   \n",
       "4      san-gabriel-valley  los-angeles      standalone-city   None   \n",
       "\n",
       "                                            geometry  \n",
       "0  POLYGON ((-118.20703 34.53902, -118.18941 34.5...  \n",
       "1  POLYGON ((-118.30800 34.03740, -118.30067 34.0...  \n",
       "2  POLYGON ((-118.77621 34.16816, -118.72632 34.1...  \n",
       "3  MULTIPOLYGON (((-118.37822 34.48811, -118.3783...  \n",
       "4  POLYGON ((-118.12175 34.10504, -118.11687 34.1...  "
      ]
     },
     "execution_count": 44,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "#survey of nbhood data\n",
    "nbhood.head()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 45,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "san-gabriel-valley        46\n",
       "san-fernando-valley       34\n",
       "south-la                  28\n",
       "central-la                26\n",
       "southeast                 25\n",
       "westside                  23\n",
       "north-county              21\n",
       "south-bay                 19\n",
       "south-county              15\n",
       "harbor                    13\n",
       "antelope-valley           13\n",
       "northwest-county          12\n",
       "beach-cities              12\n",
       "verdugos                   7\n",
       "northeast-la               7\n",
       "santa-monica-mountains     7\n",
       "eastside                   4\n",
       "angeles-forest             3\n",
       "pomona-valley              3\n",
       "Name: region, dtype: int64"
      ]
     },
     "execution_count": 45,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# curious to see how many neighborhoods per region\n",
    "nbhood['region'].value_counts()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 46,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f6447460d30>"
      ]
     },
     "execution_count": 46,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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\n",
      "text/plain": [
       "<Figure size 432x288 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "nbhood.plot()"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 51,
   "metadata": {},
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f64401f0c40>"
      ]
     },
     "execution_count": 51,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "text/plain": [
       "<Figure size 2880x1440 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "nbhood.plot(\n",
    "            figsize=(40,20),   #size of the plot (a bit bigger than the default)\n",
    "            column = 'slug',   # column that defines the color of the dots\n",
    "            legend = True,     # add a legend           \n",
    "            legend_kwds={\n",
    "               'loc': 'upper right',\n",
    "               'bbox_to_anchor':(1.3,1)\n",
    "            }                  # this puts the legend to the side\n",
    ") "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 52,
   "metadata": {
    "scrolled": false
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "<matplotlib.axes._subplots.AxesSubplot at 0x7f6439f101c0>"
      ]
     },
     "execution_count": 52,
     "metadata": {},
     "output_type": "execute_result"
    },
    {
     "data": {
      "image/png": "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CyvnJmFWcligp8MwDMp+aJL1jpz3xu3ykuU/NMtybokdlkd6bW0t78MPP7wya9asmjvvvDNpx44dstdff13x5z//ufauu+4yr1mzJnrDhg3R77//fh0A6PV66tSpU+UAUFlZybv77rsNv/jFL7rfrW63m7hw4ULprl27pJs3b45euHDhpRtvvNH89ddfi1QqlYOiKPqHH34QAcAPP/wgevTRR2v27t0rqays5J0/f76UpmnceuutKV9++aWopaWFpVAoXN9++20l4Iteh4aGev72t79FHj169FJUVNQ1VkWvvfZaeE1NDffixYslbDYbLS0tlNVqJVauXJn473//uzw7O9tx//33J7z66qvhmzZtah3otamsrOSdOHGiXK/XU2q1OvPZZ59te+211+rvvvtufllZWQkAHDx4UPTnP/858mc/+5m+o6ODKioqEu3Zs6dqOH+LYIER6BMUzexoRqB34nL0HU3kSziMQPcTDp8FQ2vfrxW782sweMKR2bW41Nl9Mjc2BFfaht+11Oby4Hy9AXw2BZvLg7wEGcx2N+q0Vz9PEYcak26b1wtFADw2BYd7aE0Nk8OFuNxmgdtL43Tt8MQ9Q/+c6mzStGSaMsAzYRguVoPTry1pi8Ex7K3rmJgYx6xZs2wAkJuba718+TLXZDJRd911lxkAHn/88Y78/PykrvHLli0b0IIpPz9fBwCzZs2yPPvssxwAmDdvnukvf/lLZFJSkvO2224zfPvttxKTyUTW19dzc3JyHG+88Ub4sWPHJBqNRgMAVquVLCsr491yyy2mjRs3xq5evTrmvvvuMyxcuHDQHLqvv/5asmrVqjY22/eSREZGer7//nu+Uql0ZGdnOwBgxYoVHW+88UYEgAEF+m233abn8/k0n893y+VyV319/TXatXMRE9/Q0MD66KOPZHfddZeu67HHK8ze2wQlJEKAWI080NMIWkgWAe8QhcxkhsW+/kuFN0hzcW0un/iu7rDC0ocQl4k4Yz2lYaGU8XFyENvE3rApApevY5HD4D9MutD4RSDluPwZJ5Ry/RrXFxwOp/sEoSiK1uv1AwZQxWLxgB9gPB6PBgAWiwWPx0MAwJw5c6znz58XHDt2TDRv3jxTZmam9fXXXw/LysqyAL5zdM2aNU1lZWUlZWVlJbW1tcXPPPNMe3Z2tuP06dMlWVlZto0bN8Z0pcb0ZMeOHSHp6ema9PR0zbFjxwQ0TYMgiKtO+oHeAxRF0V6v7ynZbLarPnC4XG7P1wZut7vPD5MHHnig491335V/+OGHoU888cT1b9cGGEagT2AyZzPFon3B5lKQKwRorRn9FucTBYp1/ZcKz0hfbUZY77eaHHD2sWhTSHh9jA5Ghv6CMJ1Exw5Gn49f0n8SpWOxyQEFMYtNetN+ohixhDCpVOqRSCServzx9957L3TmzJl9Rq5FIpHHaDQOeoXl8Xh0VFSU6/PPP5fNnz/fMnv2bNMbb7yhuPHGG80AcMcddxj/8Y9/hBkMBhIAqqqq2A0NDazq6mq2WCz2Pvnkk9o1a9a0nD17VgAAQqHQ0zX24Ycf1ncJ+zlz5lhvvfVW41tvvRXucvnWLC0tLdSUKVPsDQ0NnOLiYi4A7NixI3T27NkmAFAqlc7vvvtOAACffvrpoBZbUqnUY7FYrnrOq1atat+2bVskAEyfPn3cNz9hBPoEJj47FELp+Ij+jRVRyVKweRTa65mo4VAgR0Cgu0fwahMh5sI7RuKysEaHpCBv2BMTwoPDM/QdIZr2Rd4ZRh8ajEIfr/BEbE/WfGXTQGOy5iubeEL2iG7Lbt++vWrDhg3K1NRUzfnz5/kvv/xyY1/jli9frt26datCrVZ3F4n2x8yZM01hYWFusVjsXbBggbmlpYU9f/58MwAsXrzYmJ+fr73hhhvSU1NTNffff3+yXq+nioqK+FOmTFGnp6drXnnllahNmzY1AcAjjzzSfscdd6j6KhJ95pln2pRKpTM9PT0jLS1N895778kFAgH91ltvVefn5yenpqZqSJLEunXr2gBg06ZNjevXr4+bNm1aGkVRg75ZFAqFZ9q0aWaVSpWxcuVKJQDExsa6k5OT7T/72c+GVQcQbBDBuO02ffp0urCwMNDTmBAU7L+CwoPVgZ5GQBFIORDJePC6PYwwHyZRKdLuQtvh0pghxEcN17/ryGeTsLnGNj1JFSFCRZBaF8bJ+aBIAlXt1gHHhYu5MNhc8HhpeHosbqbHy8ZVIex45bX8HCYPPQgpLS2FWq0GABQXF1szMzNL+xt7Ym+l4sI39VE9C0ZZbNKbNV/ZNGtxSvMYTJdhAEwmE6nRaDRnz54tDQ0NDf7CoU7OnTsXlpOTk9D7dqZIdIKjuTEaRV9UT9rtVYGUA7fLg9ZqY6CnMq4hRqAbUd9Zg30TKuQgTMTxOcXQBGjCV6xp70xBudg4tn/PilYzpsaFjEgRZZiIg3Dx1UEuIYeFc/V6kATgcA/tzRom4vo1r1gZH20mR/cc+GwKIIDqDmbROhZM0kvwhGLW4pTmqbfHt5b/0CyzGBxsoZTrSvuJQjfSkXOGobNv3z7x6tWrE1avXt0ynsT5QDACfYIjlvMQnxWG6vPjvl5iyJAUAS6fBavhWrs9BiBKJYXb6ftcob00QNO+zpGdq7nuRR0NaJuvX8SFUBRuSJDB91A+Kz8vTcPrKyZCp4MjSBBgUUS3+0UX0+NlIODLm06JEMHt8cLq9KDVNDYNh9pMDrBI4Hpri0mCQGlT3/UPUj4bDrf/dWZyAQeVfkb2ewrE9j4sKBlGl2DcrWYYOjwh2ztcK0WG0WPRokWmRYsWXQj0PEYSRqBPAjLnxExKgR6ZKLnutIyJjKndDrNu7Lpp8l3Aqcbhp1L0lYahihCNmUCv09kwI1GOs3W6IUe5e8KmCJAEcL0p9NlKKRr1Nhit11gQ90lweuhMHhh9zsDAMBQYgT4JiNXIIQ7lwdQx7ouah4TNxEQJB8Izxnnco1Ek12SwITtGikaDbUyiwgVVWsgEbGiiBGCzKNCduw4skgBNA2dqdXB7adyQKEdZkxFeGlBHia/aDWBTZL/i3GBzQcRlgQAQI+OjyWCDwXatAFeG8FHSaGRcWMYRTJEoAwPDUGAE+iSAJAlkzI7GD/uuBHoqY0a0KgSNFUzTlYFwjXHzndGQJ2aHB+cbDLghQYaYED4IgkBpk3HIzXqGgs7qgs7a985MrJyPOq0NBqsLRrtPWJc0GiHlsxEu5kIu5AC0z3O9P8wO3/3Kmk2IlvLAY1Fo6WOXgBHn4wsmgs7AwDAUGIE+SVDPisbJz6vGzJoukIjlPEac+0FX/vlYMZpnXs8ItVzIgcMdmN2TrjQSt9cLuZADskdeSU2Hxe988S4aDXZkxUivEugSHgsiHgsKCQ8EAd8XCBAEQHb+v/MfCIKAx0uDTRHgsSmEi7ndhaIMY8skuPROCmwmI1Vy7GuZWadli2Ryl2bOzTq+WDIhihIZggtGoE8SBBIOknLDUVk0YEfdcY9QysEIGI5MKHgitq/REE0DhO8bRZEwacc25Wms9ImnlxK6IUGGy20WuDxeqBVinKwefUvBvrpz8lgkchNlKKrRXTPHgbjQYEBGtKTbuSZNIb6mgNbfOaWECxmBHiBI5ro07jn20XbFmUP7o9xOZ7fN4n927ojNXXhP05zlv2BsFvvgwIED4tdeey3ym2++qdy6dWtoYWGhcMeOHbWBntd4gBHok4iMOTETWqATBMDhs6BrHtgPerIhDOGgIwj838dKoKdGiuDu9PomAOisTmgtvoj6yWod8hLlOFmlHZXHHkiD2d1enKzSIiaEDyGXwqUW/6PpJrsbFAF4aMDiGH6wjsemhn1fhuuDCRyMb459tF1x6vM917TndjudZNftjEhnGEmYTqKTiJjUEIRECgI9jVFDkSxlxHkfBEvuq3eMJPqpah3O1Opxvt6Ac/UGVLZevTg5WaXFlNiQUXr0wVVYg96GqjYLksP9705aq7VCFSnGDfEylDX55wEv4lLIjQ3B9HgZpsXJcGNyKDgsErmxIciNC8GU2BDkxkqhjhIzDi9jwEj0EmAIDDaTkTpzaH/UQGPOHNofZTebhqWpysvLOYmJiRmLFy9OSE1N1SxcuDDJZDKRn332mVitVmtSU1M1+fn5CTabjQCAmJiYrKeeeipmypQp6ZmZmer//Oc/gpuPAh6EAAAgAElEQVRuukkVGxub+T//8z/hAOD1erFy5UqlSqXKSE1N1bzzzjsywBfRzsvLS1u4cGFSYmJixr333pvo9frSHdetWxeVmZmpVqlUGcuWLYvvur0n2dnZ6YWFhbyun/Py8tKOHz8u+OabbwS5ubnparVak5ubm37u3LkBO5o2Njaybr/99uTMzEx1Zmam+t///rfQ4/EgPj4+s7GxkQUAHo8HcXFxmU1NTZMymMwI9EkEQfiKRcc7LA6JaJUUoTE/Chy+hIOOxuDs9MjQCR08AqW4QQ91lHjEj+uvBnN5aQg4Q/vMKWs24VSNDlIBe8BxkWIu8hLl8NDAmTo9Cmt0KKrV4bvLHThdq8eZOj3O1Opxtk6PM3UGlDaZkK2UDmkuDEOHZAT6uKXk2NeynmktfeF2OsmLx76WDfcxqqureatWrWq7dOlSiVgs9v7+97+PXLlyZeKuXbsuX7p0qcTtduPVV18N7xofGxvrPHv2bNmMGTPMjz76aML+/fsvFxQUlL388svRALBjx46QCxcu8EtLSy9+9dVXlzZt2qSsqalhA0BpaSn/jTfeqKusrLxYW1vLPXz4sAgAnn322dbi4uLSioqKizabjdy5c+c1F4YlS5ZoP/roIzkA1NTUsFtbW9mzZ8+25uTk2E+ePFlWWlpa8pvf/KZh/fr1A7bNXblyZezatWtbiouLS//5z39eXrVqVQJFUVi6dGnHu+++KweAzz77TKJWq21RUVH+eclOMCblqmQykz4zCj/suwLPKLpc+IMkjAcOj4X2+qGLanm0CI0VPhcNgZQDaTgfZp0DNiNjq9gXQSMLiCAJ5cPXbKhRb0OcXIBa7fjadZHy2YgO4aPV5IDHS8Noc2FavAytJgdC+Gycq9f36foyEOfqDZiVFIoTV5j+K6PFZCjQn6iYddqBV8WdWPwc1xcKhcJ52223WQDg5z//ecdLL70UpVQqHdnZ2Q4AWLFiRccbb7wRAaAVAB544AE9AGRlZVktFgspk8m8MpnMy+Vyve3t7dTx48fFDzzwgJbFYiE2NtY9Y8YM83/+8x+BVCr1ZmVlWZKTk10AkJGRYb18+TIHAL788kvxn/70J4Xdbif1ej1Lo9HYAFxlWfXwww/rbr311tQ///nPjTt27JDdc889OgDQarXUT3/608Tq6moeQRC0y+Ua8KPnu+++k1RUVPC7fjabzZROpyNXr17dfu+996Zs2rSp9f333w9bsWLF5Gvi0gkj0CcZPCEbqukRKPshsKlyfAkHLVeMiEqRDrmZEIv9YyDDanAynUIHIVgCd0TwLBUAAAabG1wWhTARZ8Q81CMlPESIefBl3BO+7wQBh8uDc/UGpCtEkPI5AIBGg21Yj2F2uK+xaSwYgZz6gmot0iPFKGvpu8spA8NkRSST+9XeV+jnuL4YagoUj8ejAYAkSXA4nO7VH0mScLlcxECda7lcbvcvKYqC2+0mrFYr8etf/zq+oKCgJCUlxbV27dpou91OVlZWsu+++24VADz66KNt69evbwsJCXEXFBTw9+7dK9+2bVsNAGzYsCFm7ty5psOHD18uLy/n3HzzzWkDzZ+maRQWFpaKRKKrJiqTybxhYWHuzz//XHzmzBnhvn2TyB+6F0yKyyQka/6AO09jQmu1EXwJB6YOGwQSjt/34wpYMLQPT9hMVujAbpZ0E1zy3EeryQERlwUhZ2SKJwuqtDhZrcXJat2P36u0YLNI8FgkJHw2Cqq0KKjSok47vPN4tBoyebw0dDYnxFymkHQ04I3QOcYw9mjm3KxjcTgDXklZHI43Y87Nw7aIampq4hw5ckQIAB9//LF83rx5xoaGBk5xcTEXAHbs2BE6e/Zsv1fPc+fONe3evVvudrvR2NjIOnnypGj27Nn9ugVYrVYSABQKhdtgMJD79++XAUBKSoqrrKyspKysrGT9+vVtALB06VLtli1bFCaTicrLy7MBgNFopJRKpRMAtm3bFjbY/G666SbjK6+8EtH184kTJ7qj6Y8++mjbY489lnjvvfdqWazJG0dmBPokJCJeAkWSJKBzoL1ASAQfZp0TbrcH0arBc2AFUg7YXBKWMWxPPxEgWcHxNg9GgQ74mgbFhwoQKRmwpum6KKzWdbq4jL7F4/XQYnQgKWLkc/MZAE8fBXcM4wO+WOLJXXhP00Bjchfe08QTiYf9R05KSrK///77oampqRqdTsd64YUXWt96663q/Pz85NTUVA1Jkli3bl2bv8f7+c9/rs/IyLCp1eqMefPmpf7ud7+rj4uL6zeXOywszLN8+fI2jUaTcccdd6Tk5OT0K+Z/9rOf6Q4ePCi/7777urfuNmzY0Pzb3/5WOXXq1HSPZ3Cnqbfffrvu9OnTwtTUVE1ycnLGX//61+78+mXLlhmsViv1xBNPTOqcuwG3QQLF9OnT6cLCwkBPY0Jz6VQzDr9XEtA5UGwS0jA+eCIWmi4bwGKTkITxYdE7Ybdcu1MYpZKiqWJo6TAMQES8GK01gU9bsGeI8b8NwWvzKeJSkAu54y4nfTRIChP6ilE7M3U6k3W6F1kEiO7W9V2NkXpC9PgP0XlvgvCZ8BMEcdWxevNjchAN0EB5iwkG2/ivEfufJdl44IbYQE+DoRelpaVQq9UAgOLiYmtmZmZpf2P78kFncTje6/VBLy8v59x9992qioqKi8M9xkTi2LFjgmeeeSa2qKioPNBzGQvOnTsXlpOTk9D79sm7dzDJSc6NwHeSSlgDWFjpcXmhbfIt0rvEd0eDBRHxYkgj+GiputpOzusOvsUkw8TB7PBAyPFALuR0+6ZPVq60B943v4sYGR88FjXkwtdgw8VE0Mc9c5b/ojnvvqWtF499LbPotGyhTO7KmHOz7noi5wxX8/zzzys++OCD8O3bt1cFei6BhhHokxSKRSJjTgxOHQiO94CxzY5oVQgaK/Td0V5xKA+mDl+3S3m0sFvMMwyRIMgt8XJJVI9eBsmI0WJyIDlcCJPdBZeHWRAGAw06G8LFXMTK+KjTjd/6EzdzPk0IeCKxd9qd941o6kVaWpqTiZ772LJlS/OWLVuYhk9gBPqkJmN2NIq+qA4K+y+PywuLwQGCAujO9DUOjwKLQ0Is58HQaoWHiaAPjwC8bDRoeCVs2EM50AsJHDeZEUOPjzSFy20WZMVIcaGBSacKFtpMDoh5LEyLl/3oSjTAed37V133IdCVkkP7fPk7s3O0FicqWke3j4LLwwRZGRgY/IcR6JMYoZSLpNxwVBYFLi+4My0VdosLdosLsRly2E0utNWa4LC64HZ6me6gQ4DFIRERL4Hb5YHHRcPr9ULXMnavn0dEoSaRh287jOiwmgAdAB0wI1GOjnGUNkIASIsUAYQvg5rozKXuEnokQVwl+rrGlbeYYHMOXiDFMHRMdjeKakanyJYiCdyYHIrvr3QgCOIVDAwMDIxAn+xkzo0Zc4EujxKCzaPQWmMESRLdkfGoFCnqLmoRkxYCkYwLxwQoDBtrwmPFaKzQj/njeoQkriTz8a8mHWx110Yi280OXG4bPylK54cZPY+R8dHgHL9pGJMVj5fGd5c7oI6SQG91oMkw8vnuQejHwMDAEMQwAn2SE60KgSxKCN0Y5nezuBRaq40gKQIki4Q0nAdtswUuh0+Qez00WBwKZsZOcchYRkFYDIYrjIPtLAsMtf2fQxLe5LjUBEG6P8N1UNpkhJjLwg0JMpyqHtlovZdR6BMCm8lIlRz7WmbWadkimdylmXOzji+WMNtmDCNOcBgkMwQMgiCQOSdm1B+HYhEIjRaCJ2bD4/KApgGPm4bL7oGuxQK+iI32Op/A68tikWFwSBYBk84+5o9bH8WGwT7wbgeHNTmatDACffxjcrhxqlqHvAQZRCPYXIiR5+OfYx9tV7z95Irsb3e8G1+4f2/0tzvejX/7yRXZxz7argj03Hpz5swZXnp6ukatVmsuXrwY8BL9tWvXRm/atClytI5fXl7OUalUGQBw4MAB8fz581NG67HGCkagMyDtJwqwRrl7oEjGQ0ejBQQAl/PqYinaC9hMP4pyXZMVFoMDPBF7VOc00fC6abAD0AXS4of0mDTRQ0ahTxhOVusgEbCRrhiZxk2T5S0wUTn20XbFqc/3xPT0QAcAt9NJnvp8T0ywifT/+7//C7njjjv0paWlJRkZGX5trbrdTFppMMEIdAZw+Syk5g1/YSuPFv7orNAJ0evMEkg5AICQSAGMbYPn6LrsHsiihMOe02SFzR5bge7hkjirH9z9wuLwQMihwGORYFPEhNWxE/eZTU4a9XZUtJoxMyn0uv+yk2aROgGxmYzUmUP7owYac+bQ/ii72TQsTWU0Gsl58+alpKWlaVQqVcY777wjW7duXVRmZqZapVJlLFu2LN7b6aOfl5eXtnr16pisrCx1QkJC5qFDh0S9j7dr1y7p22+/HfnRRx+FzZgxIxUA3nzzTXlWVpY6PT1d89BDD8V3iXGBQJC7Zs2a6Ozs7PSvvvpKJBAIcv/rv/4rJi0tTZOTk5NeV1fHAoCPP/5Ymp2dna5WqzWzZs1K7bp97dq10fn5+Ql5eXlpSqUy68UXX4zomseGDRsUCQkJmbNmzUqtqKjojuKfOHGCn5OTk56amqpZsGBBcltb2zUfXHfddVfSrl27uluML1myJOGDDz4IKS8v50ybNi1No9GoNRqN+vDhwwMKBaPRSObn5ydkZmaq1Wq15sMPPwwBgGnTpqWdOHGC3zVu6tSp6QUFBfz+jzT2MAKdAQCGleYiDuUhPE4EbaMFwhAOIhLEYHMpcAUshClFYHGuPb3a6/zvaEkztmRDgmKTsFtHPz3IyyJgTBGgNlOIf0bTaPKjgUxJkxEWpwd2txcuD428RPmoz/N6SQ4XYnq8rPtrWufX1LgQ3JAgC/T0GMYIj5fG91c6kB4lhkIS8EwBhgBQcuxrWe/IeW/cTid58djXw7ow7N27V6JQKFzl5eUlFRUVFxcvXmx89tlnW4uLi0srKiou2mw2cufOnd1i1e12ExcuXCh95ZVX6jZv3hzd+3g//elPDQ8//HDbqlWrWgoKCi6dPn2at3v3bnlhYWFZWVlZCUmS9FtvvRUKADabjczMzLSdP3++7PbbbzfbbDZy5syZ5vLy8pKZM2ea//d//zccABYsWGA+e/ZsWWlpacnSpUu1mzdv7t4xqKys5B09evTSqVOnSv/4xz9GOxwO4vjx44J//vOf8gsXLpQcOHCg8ty5c91CesWKFYlbtmypv3TpUklGRoZtw4YNfT0H7a5du2QAYLfbie+++06ydOlSQ3R0tPv48eOXSkpKSnft2nXlmWeeiRvotX3++eej5s+fbywuLi49fvx4+QsvvKA0Go3kihUr2t99990wADh//jzX6XQSM2bMCKoK/8lRucUwKOGxYiiSJGi+YkRYnAieAewNCQKITJJC22iBQOKLjJt1Tpj1TohlPIhDeTDrHQiNEXV3A3U5PBBIObAa/LfaI3qH5ceAkEg+9C1B9R71G4/LC4pDYrSyXWnQ0KeKsN9mQkv79fXpMDuCfytVxKFQ2I+t35RYaZ+3B+CUZRgjSptMEHNZmB4v6/e8GIhg6DfBMDzMOq1f+ZYWP8f1ZurUqbaNGzfGrl69Oua+++4zLFy40PzBBx+E/OlPf1LY7XZSr9ezNBqNDYABAPLz83UAMGvWLMuzzz7LGez4hw4dEhcXFwtycnLUAGC328mIiAg3AFAUhRUrVnSf0Gw2m37wwQcNADBt2jTLkSNHJABQVVXFWbRokbKtrY3tdDrJ2NjY7sjMbbfdpufz+TSfz3fL5XJXfX0965tvvhHdeeederHY12X1tttu0wNAR0cHZTKZqLvuussMAI8//nhHfn5+Uu85L1261LB+/fo4m81G7NmzR5qXl2cSiUR0R0cH+ctf/jK+pKSET5IkampqBlw1f/vtt5J//etfIVu3blUAgMPhICorKzkrVqzQvfrqq1EOh6P+rbfeCnvooYfaB3sdxxpGoDN0kzVPCYJsQEuVEaExV+8akSwCklAe+GIObCYXmi/7bOhcDg+kETzQXgIOmxPiUB4aK/UA7UudkUcLweZQaKk2QhLGA0H6cs79YozUjkDKQUiEABaDA3wJZ9wKdIpNwuMcnV0HZwQHx+U0TjePzDXMaAv+QmA2i4QqQtRnAxsmW2FyYnK4UVijw/QEGUobfbtC/sKcMuMXkUzu1wVL6Oe43mRnZztOnz5dsmfPHunGjRtjjhw5Yty+fXtEQUFBSUpKimvt2rXRdru9O4LP4/FoAGCxWPB4PAQALF26NKG4uFgQGRnpPHr0aGXP49M0TeTn53e88cYbDb0fm8PheFmsH6Ugi8WiSZLs+j/cbjcBAE899VTcr371q+bly5cbDhw4IO4Zuedyud2nN0VR3fcZSpDN7XYjMzNTAwALFy7Uv/76640/+clPTHv37pXs2rVLtmzZMi0AvPTSS5ERERGuPXv2VHm9XvD5/GkDHZemaezevbsyJyfnmq3e2bNnGz/++OOQzz//XF5UVFTi92THCCbFhaGbpNxw6Jqt8HpotNWZEZkkQXRKCKKSpaAoEvpWG5oqDdD3aHyjbbTA0GqHsd0GeZTI58Hd+VZtqzVB22hBS7Uvim5st0MSxvN7Pg7r6De2EUg5oGmgsUIPQ6ttXGcQ84QjW1Tr5ZEwJQlQnCXAG24jTjcbR+zYFDkOXmmCgIjbdwyjstWMxDAhEkIFSAgVIL7zK0rq//nNMH4prNZBymf7mln5CZODPn7RzLlZx+JwBox+sDgcb8acm4flzVldXc0Wi8XeJ598UrtmzZqWs2fPCgBAoVC4DQYDuX///kFTZ3bv3l1dVlZW0lucA8DChQuNBw4ckDU0NLAAoKWlhbp06dKgkfeemEwmKi4uzgUAH3zwQehg42+++WbzwYMHQ8xmM6HT6cjDhw+HAEBoaKhHIpF4unLn33vvvdCZM2eaWSwWysrKSsrKykpef/31RgB48MEHtR988EHYqVOnxIsXLzYCgMFgoKKiolwUReHNN98M9XgGXiTPnz/f+Nprr0V25fB/99133Xnmq1atat+wYUNsTk6OJTIyMuisMpkIOkM3LDYFzY3ROP2vGoAGWq4MTZCZtQ7Io4XgClhoquy70ctQVtSG9tG3DBTLed1pOMD4joxy+BQsI9SjyJQkwIcWA8xaC6AdmWP2ZDwIdAJAg77v3RSL04Oq9mt93zksEjN65Nd3nU8E4UsR6iojpTuP3/N06/2KjEX7eYbh02iwgzIR+EmSHAVXtINGyMfztWWywxdLPLkL72k69fmefou1chfe08QTiYe1hVlUVMR/7rnnlCRJgsVi0W+++WbN7t27QzQaTYZSqXTm5ORcV6OSadOm2V944YWGW265JdXr9YLNZtNbt26tTU1N9TsKtnHjxsZly5YlR0ZGOqdPn26pra0dMLXkpptust5///3azMzMjJiYGEdeXl73xWz79u1Vq1evjn/66afJuLg4xyeffFLd1zHuv/9+46pVqxJvvfVWfdeuwZo1a1qXLFmSvG/fPtlNN91k4vP5A77mL7/8cuMTTzwRl56erqFpmlAqlY5vvvmmEgBmz55tFQqFnl/84hdBl94CAAQdhFeN6dOn04WFhYGexqTE2G7DP/77+2Hvx5IsAtJwPhxWd5/55qExQnQ0DH6tYfMouOyjs6AVybhwu7ywm10IjxWhrbPzZVeqSyA6cY4E0nA++J01AT+qAZ8MJDoFcZfLCA0auiYL7BY3aAqguRTgoeERkGiO4WJPUwdcntG7NigkPMTK+SBAoMMy9l1GCQAU6VswUgTRvWBwebxwe2l4aXQ3q5ELOdBaRn83pzeaKAlKmkZu14Jh9EhXiKGzOtFi7L9g+umbU7D2trQxnBWDP5SWlkKtVgMAiouLrZmZmaX9jT320XbFmUP7o3oWjLI4HG/uwnua5iz/RfMYTJdhBKmurmbPmzcv7fLly8UUFbheHefOnQvLyclJ6H07E0FnuApJGB8JmaGovjC8IkCBmANdU9/FpQBAUv5FTl12D0QyDsy6kRVGPCELVpMTklA+JKG8q/LcxXLeuBXnAGBos8Hgh4VlF6I4Ib6NI3GqqcduBw2g3n+nneHSbLSj2ejbIclLkPcp0FMjRbA5PXB6vAgTcXGxcWTEqpjHgsnuhtsLADRc/axGuwoBlTJ+QAS6aJJ0X50IlDX7CkinxclQVNt3lkPwhcIYhsqc5b9ozrtvaevFY1/LLDotWyiTuzLm3KwbbuScIXD89a9/DX3xxRdjtmzZUhdIcT4QzCcAwzVkzlUOW6DbTAMLGVOH/63ohTKe3wKdw6fgtA0ccRfJuBDJeWi+/GMe/dUZN/59hEarQmBotYJiUzC2j8+CUgAolAOnqvtORRpLSpuMiJXxwWVT4FA+n3SKJHCu3gBPp/OF0eZGvFyAGm3/iz9/YVP+ld50bULwx9hbvosG3fg9tyYjJocbRbU6TI+XobTp2gJSJgd9YsATib3T7rzv+mysGALOU0891fHUU08F9d+REegM1xCnkUMSxoNxGDngHjeNqGTpVQm1NpMTLA4FDo8Ft9MDiiJgMQ4uvL1u/4ISoUohTO12UGwSYjnvqiLWngik3G73mS56fmbSNIFolRQOmxssFgWSTQI03Z1PH6YUwusF2upMcNk9iFKFBFSgR6lCrprfUDClCHGoLjiuTSaHG6ZBbBdtLg8k/JG5XHH83MXpIlCWkDRo8NkUbK6gq11iGIDCGh2ipTzEyPi41PJjDQGjzxkYGIYCI9AZroEgCWTOUeLE3muKwf2iqZcIjkyQdDu5AABXwEJUis9HmvbSaK4yXhO8jk4J8dk1DjZXCvC4aDg789X5Yjb0LdeOC4nko7Vm4BSJ1uprf88T/eiMYre4Ydb9uAPQ5Mf8RhOv2wu7ZeiuXlVZQuyuC8qamAHhUOQ1hZXDgeVnBL2L2o7rj9oPh0a9HXkJcpysHoUqXYZRpauAdEaiHCerfAWkjA06AwPDUGBsFhn6RD0rChR7ZE6Pll7C12F1o6nSgKZKA5qvGBGZILkq1YQnZMNqdl5ra9EHnF42eF5335+CAgl3WMrObnYhVCkET8S+pjNqaIz/FmsjDV/Mhklr7/f59ocrlD0uxTkAFNXqQQNgUwT4HApiLgshfDbkQg5y40LA9jMyzhqig4zJ4UZKxIDdpEcNDxN2Hbd4vDQKqrRIVYgRKeZ2uvgwMDAw+AcTQWfoE56IDdX0CJR9P/zCdJGcC9pDwzJI99CWKiNkUQJweCzQXhqtNSbYLS5EpUgHTd9wWN2QhHfbmsLQT8pJlwfqcGBxKPCEbJC9hB2HH5jcZJlCAGO7zZdOlBICk9a/VCQaNEpi2EDtKE9wlHF5aLh6ed92FXFyWSQkPDaEXAp8DgUOi/LltHeuALv0bvUQo+KcABURBaPLFsPQKG82QcRlQcwU/U4IPFYXZS1qlXlMDjYl5roE0yJ0lIDN5KExjDhMBJ2hXzLnKv0aR1BARIIYFIcEV8ACR+ATM0IpB5IwPqJSpCApAkIpB0Q/Z5yuyYqWKiPsFl++ryJZgo56M5TpMkSlSBEeJ+738TvqzeAKfR9+ktBrG8UQFK6rO2jLFSP0LVZom652GiECoJ2iVVKwuFT3osTt9CBaFYKoFCki4vt/jTx8CmezBPh3bXDknY8WDrcXbWYHqjusKG0y4VydHoXVOhRUaVFQpcXJau2wUkZKmoyYGhcy5o2sxoNfPMPgmB3ugKVKMYwc+i+qFM1/OJltOHgl3nysIdpw8Ep88x9OZuu/qFIEem7Xy4EDB8Tz589P8WfsT3/60/iioqIBu7Ll5eWlHTt2THC981q7dm30pk2bIgFgyZIlCdu3bx+0adNEgVnSM/RLZIIEEfFitNYMbLtHe4DW6s4xXhoiORdiGQ8kScLj9kLbZEFYrBit1UZEq6RorOg/Km5st0GRJIGx3Q6n3QOrwQldswU0DSiSJHDaPN1i3GpwgqQIcPis7iiyy+GBTCEAX8xGW50ZLrsHfBGnT0/260U/BEvD64XFIRESKUBbnRmSUH5319C22h//NvLovtMwDClC7LUZ0V7HNL25Hk7X6pEbF4Jzdfoxyyeu7bAiNy4EZ2rHr/0ngw+DbVhd4BmCBP0XVQrzsfprGhXRLi/ZdXvInYkT3gvd7XZj165dNYGex2SAiaAzDIi/UfQuPG4ahlY7OhosaLpsQGuNCeJQHlqrjWDzKDisgztiNF8xdgtqbZMF8mghRDIumq8YoW2ydOevG9ps0DX7Iu9d47tua6wwgKJIRKVIweWzwOaOXIqCIkkCWZQA3BFyFRkInpANEIDb6UV754Kjo8HcZ+pP7xQcAGjRCPF2ezvaA+DjPRE5U6tHtlKKIRrBDJsWkwPF9QbEh153IIohwDACffzisbooy/eNUQONsXzfGOW1uoalqYxGIzlv3ryUtLQ0jUqlynjnnXdk69ati8rMzFSrVKqMZcuWxXelaebl5aWtXr06JisrS52QkJB56NChPouhjh49KkhNTdVMmTIlfeXKlUqVSpUBAOXl5Zxp06alaTQatUajUR8+fLg7smMymagFCxYkJycnZzz00ENxns5UQoFAkLtmzZro7Ozs9K+++krUMzq+d+9eyZQpU9I1Go36jjvuSDIYDP2+Bh0dHVRMTExW13FNJhOpUCiyHQ4H8dprr4VlZmaq09LSNLfffnuyyWQa8LU8fvy44IYbbkjLyMhQ33TTTaqamhr2xYsXuRqNRt015sKFC9yMjAz1QMcJZhiBzjAgqukR4AquT4iyuRQoFgG3y+NXF9HedDRYYDM5Ea2S9vItvxZvj+6XdosLTZUG6JqtcDlGLkXQanRB12SFrtmKqGQpolKkiEyUXDMuMlECmeL6hJXb5fG/uLXXa+MM5+CfHVVx6ocAACAASURBVEzkdaQ5W2dARrQU7DFKP3F5adicHoi4zIbneEZvZQT6eMVa1CqjXd4B9RLt8pKW063DSr/Yu3evRKFQuMrLy0sqKiouLl682Pjss8+2FhcXl1ZUVFy02Wzkzp07pV3j3W43ceHChdJXXnmlbvPmzdF9HfOxxx5LfOONN2rOnj1bRlFU96dIdHS0+/jx45dKSkpKd+3adeWZZ56J6/rdhQsXhH/5y1/qysvLL1ZXV3N37NghAwCbzUZmZmbazp8/X3b77bd3b8U2NTWxtmzZEnXs2LFLJSUlpVOnTrX+/ve/j+zveYaGhnrS09OtX3zxhRgAdu7cKZ07d66By+XSy5cv1xUXF5eWl5eXpKWl2bZu3RrW33EcDgfx9NNPx3322WeXL168WPrII4+0r1u3LiYjI8MhFos9J06c4APAtm3bwh566KFxm9fJCHSGAWFxKKhnDRg4GBSKIsEXc0Bfh0b2uGk0VhggCeND3Eee+ZjSQ5e1VBnRVGmARe8AQV3d+MjUYQdPzL72/r2g2ESfufmKZCncTv+KWwkCoFg/HsSUJMD7pGVQf3GG4XG+wYA0hdhv55jrpdXkQKycD4U0wOc+w7AxMhH0cYvH5Bj8Qg7AY3T6Na43U6dOtR0/flyyevXqmEOHDolCQ0M9X375pTg7Ozs9NTVVc+LECXFxcXG3G0J+fr4OAGbNmmWpr6/n9D5ee3s7ZbFYyAULFlgA4JFHHukuvHE6ncRDDz2UkJqaqsnPz0++fPly90UlKyvLotFonCwWCw888ID2+PHjIgCgKAorVqy4pkXut99+K7x8+TIvLy8vPT09XbNz587Q2traa+bTk/z8fN0nn3wiA4BPP/1U/uCDD+oAoKioiD9t2rS01NRUzZ49e0IvXrzY78Xu/Pnz3IqKCv7NN9+cmp6ernn11VejGhsb2QCwYsWK9nfeeSfM7Xbjs88+k/3yl78ctwKdCckwDErm3BicPVI37Pv39kW/HgxtNvCE7GE3UhoJTB02EITPEcTbmYzc0x+9C6vRiZBI/jW398bjokFSBMLiRFfllDdfNmAw42+aoEHQBCISJGhvs0CXKkQxy42Cpg6mMcooU9xoRFaMBBcaBvbXHylKm0wgAGRESyDislBQxfijjyeYFJfxCyXm+vXHoyScYf2Rs7OzHadPny7Zs2ePdOPGjTFHjhwxbt++PaKgoKAkJSXFtXbt2mi73d4dgeHxeDQAsFgseDweAgCWLl2aUFxcLIiMjHTu3r27qr/HeumllyIjIiJce/bsqfJ6veDz+dO6fkf02qLu+pnD4XhZrGvlIk3TuOmmm4z79+/v9/F27NgRsmXLlmgAePvtt6uXLVum37x5c0xLSwtVXFwsuOeee4wA8MQTTyTu3r27cubMmbatW7eGHj16tF/XA5qmiZSUFNvZs2fLev/ukUce0b3yyivRO3fuNGVlZVkVCsW4ddhhIugMgyINFyAuQx7oaXRjt7jgtHsCFkmnvf53BexvWLQqBIpkKZRpvh1Rr4eGvtWKyESJrzg3QexzZennADRoaNOEeD/Kgws5AnwhduGvQjvebW3HD416RpyPEboxTlugAVxsNKKgSou0SBFSIwPnxc8wNCxOD1ye4du9MgQOwbQIHcEmB/zjEWzSK5wacU2U2R+qq6vZYrHY++STT2rXrFnTcvbsWQEAKBQKt8FgIPfv3z9o6szu3bury8rKSo4ePVoZHh7uEQqF3q+++koIAP/4xz+6P8ANBgMVFRXloigKb775Zqinh2XthQsXhGVlZRyPx4Pdu3fLZ8+ePaBDxLx58yyFhYWi4uJiLuDLKT9//jy355iHH35YX1ZWVlJWVlYyZ84cq1Qq9ebk5FhWrlwZd8sttxi6hL/VaiXj4uJcDoeD2Llz54CCIzs7267VallHjhwRAr6Ul8LCQh4ACAQCeu7cuYa1a9fGrVixYnw2/eiEiaAz+EXmXCVqLwZPxM5udoEgAJGMA7MueAsgvR4aIZF8uBweWPQ/ztNqdELfcrXtmsvuQUvV4NFYWywPxwUenGvxXXsO1YzbHbxxT3QIH/W6sXPz6Ul5ixkKCbd7N4ch+DHYXAgTcQcfyBBUUAK2RzgzuqkvF5cuhDOjm0gBe1grsKKiIv5zzz2nJEkSLBaLfvPNN2t2794dotFoMpRKpTMnJ2fIxVvbtm2rXrVqVbxAIPDeeOONJrFY7AGANWvWtC5ZsiR53759sptuusnE5/O75zxlyhTzr3/9a2VZWRl/xowZpp///OcDFjFFR0e7t23bVv3ggw8mOZ1OAgB+85vfNGRnZ1+7pdyDBx54QPfoo48mHThwoLzrtv/3//5fY15enjomJsapVqutZrO5X2cHHo9H79y58/LTTz8dZzKZKI/HQ6xevbpl+vTpdgB4+OGHtV9++aVs8eLFY7O9OUoQwdgIY/r06XRhYWGgp8HQA6+Xxj82nugzlSOQyKOF0DYOvfB0rIlIkKC1s6OqTCGArnlonsheLglrNBfnBV5818AUfgYLNyTIcKp6WEGzCTUHBv/46tdzkRzO7HoEE6WlpVCrfUYfxcXF1szMzNL+xuq/qFJYvm+M6lkwSrBJr3BmdFOwWSwaDAZSKpV6AeD5559XNDU1sbdv3z78XNVxxKZNmyINBgP1l7/8pTHQc/GHc+fOheXk5CT0vp2JoDP4BUkSUN8YjVMH+k01CwjaRgvk0QJoG4O7CYiu2YKQSAFA03DY/C/cfD/GA7eXhsHmAmWwwqMLvgX1ZKbZGJg6iJ6cqtZBGcKH0+NFqym4FtAMV8M4uYxvQu5MbJbMU7ZaTrfKPEYnm5JwXMKpEbrhRs5Hk08//VT62muvRXk8HiImJsbx8ccfVwd6TmPBggULkmtqarhHjx69FOi5XC+MQGfwG/WsKBQerArC7fTg77bosnugtw99EfFog2+XjwaFukwR/tmshdMddJ8Fk5Y6rQ2RYi5aAiyM6/W+ebBIAu6x6qLEMGQYJ5fxDylge8U3xQR9XuHjjz+ue/zxxyfd1trhw4cvB3oOIwVTJMrgN2I5D3GZoYGexjVoGy3X7Tce7BAgoLxoRmYYsz0ebMSHCcEKgitpi8mBqXEyCDgj15SLYWRhnFwYGBj8JQg+VhjGE5ob++yJEHB4omHZz44rSDr4dwomIyertJgaHxwuRyertZDwWFBIGL/0YERvDd6CdgYGhuCCEegMQyIhKxQC6YB9CMacaFUI7BYXOPyJHznMc7KxMC74djEmO3ZX8FjtNhsdEPNY4LGZy3uwYRhC/QkDA8PkhrmCMwwJkiKvu7PoSEGxCEQmStBYoQdPyIY8WhjoKY064itWKB1MJD3YqGqzYEpsSKCn0U1FqxnZMcEzHwYfTIrL+MdjdVGm4w1h+i+uRJmON4R5rK6JHxliCAiMQGcYMsGQ5sITsSEJ46Ot1gRFkhRNlQa4HZOjeJJ0M0WAwYbJ4Q66AsCLjQawKWYxF0zobUyKy3hG/0WVovkPJ7MNB6/Em481RBsOXolv/sPJbP0XVYpAz+3EiRP8Xbt2SQM9jy7WrFkTvW/fvn67gQYr5eXlnLfeemvQnMXq6mr2woULk0ZzLoMKdIIgeARBnCQI4hxBEBcJgvhdr9+vIwiCJggibIBjUARBnCEI4sBITJohsEjC+IhVD9rYbNTgi9kQybigaUAazkd7va/ZWXu9GRzBxA9mEK7JsRAZb1xptyA5PHh2cSxOD5OLHmQE2yKOwX/0X1QpzMfqY3p6oAMA7fKS5mP1MYEW6YWFhYKDBw8GjUB//fXXGxctWjRgJ9JgpKKigrtr165BBXpCQoLr0KFDV0ZzLv5E0B0AbqZpOgfAFAALCYL4CQAQBBELYAGA2kGO8SsA/Zr/M4w/Mmb321Bt1LGZXGivM0PfYoWu2QqZQoioFN91SR4VPAJpJNGrhDiTxYeHR4Ji9HnQEiIIrvqMSEagBxVMisv4xGN1UZbvGwfM7bR83xjltbqGlZVgNBrJefPmpaSlpWlUKlXGO++8I1u3bl1UZmamWqVSZSxbtize6/Vd+PPy8tJWr14dk5WVpU5ISMg8dOiQyG63E3/4wx+i9+/fL0tPT9e88847sm+++UaQm5ubrlarNbm5uennzp3rs4VtXl5e2i9/+cvY6dOnpyUlJWUcPXpUcNtttyXHx8dnPv30093b5b/97W8jVSpVhkqlyti8eXME4Is2JyUlZTz44IPxKSkpGTfeeKPKbDYTALBkyZKE7du3ywDg6NGjgtzc3PS0tDRNVlaWWqfTkeXl5Zxp06alaTQatUajUR8+fLjPD+8lS5YkLF++PG7GjBmpSqUy6+DBg6L8/PyEpKSkjCVLliR0jdu2bZs8NTVVo1KpMlavXt0tUAQCQW7X/7dv3y7rus+SJUsSVqxYEZubm5uuVCqzuua6cePGmMLCQlF6errmd7/7XUR/8ywvL+eoVKoMANi6dWvobbfdljx79mxVfHx85qpVq5QA4Ha7sWTJkgSVSpWRmpqq+d3vfhcxlPNiUB902tdq1Nz5I7vzq2uP/c8A1gP4rL/7EwShBHAXgJcArB3K5BiCl4ScMPAlHNiMgd+ytZtdEMp8156JmuZSyfXimzoteKpQJHYET0Eiw9UU1egwPUGGwiDp7OkNvqYFkxqmUdH4xFrUKusdOe8N7fKSltOtsuF4pO/du1eiUChc3377bSUAdHR0UG632/jHP/6xCQAWLVqUuHPnTulDDz1kAAC3201cuHChdNeuXdLNmzdHL1y48NJzzz3XWFhYKNyxY0ctAGi1WvLkyZNlbDYb+/btE69fv175r3/9q0+PcA6H4y0sLCz//e9/H5Gfn59y6tSp0oiICHdCQkLW888/31JRUcH9+OOPQ4uKikppmsa0adPUt9xyiyksLMxTW1vL+//svXt8VPWd//86t7lfMrlPMrlAwuRKAgRjFRDQsq2otBrR1iLF2gu4X3exotb1V7SudpeH7a6rW6q1rS5KV63QUlHY8vACCBSaIIHcQyD3yXXumfs55/fHkEDIJJkZkkyin+fjoSRnPuec98kkZ97n/Xl9Xu+33nrrwo033ti2du3a+bt27dI99NBD5uFjezwe6jvf+U7O7t27W1auXOkym820SqUSWJYNHD16tEmhUIjnzp2Tfvvb355fU1MTspBrs9nYEydONP3hD3+Iu/feexd8/PHHDWVlZe6SkpKC48ePy9PS0gLPPPNMelVVVX1SUlJgxYoVxjfffDPu/vvvn7Dtdm9vL1dZWdlw5swZ2Z133pn7wAMPWJ5//vmuX/7ylymffPLJeQBwOBx0OHHW1dUpqqur6+RyuZCbm1u8bdu2XpPJxJlMJq65ubkWAAYGBiKa4g/rae+SROUMgD4Ah0RRPElR1DoAXaIoVk+y+4sIJvFfzMzpSwozixaLOswe9LTYAAAMR0Ou/uJZLi4578WKdB2qHS7YtaS/2GymusOKAn3spZdxCg71pjk3w/yFhlTQ5ya8wxvWhwpv90X14bNkyRL30aNHNVu2bEk/ePCgKiEhgT9w4IC6pKQk32g0Fh4/flxdU1MjHx6/fv16CwDceOONQ52dnSGn7cxmM7N27dqcBQsWFD3++OMZTU1N406n3XnnnVYAKC0tdefm5rqzsrL8crlczMjI8F64cEHy6aefqtauXWvVaDSCVqsVbrvtNssnn3yiBoD09HTvjTfe6AaAxYsXu1pbW0dV6s+ePStLTk72r1y50gUA8fHxAsdx8Pl81H333ZdtNBoL169fn9PS0jJufLfddpuVpmksWbLElZCQ4C8vL3czDAOj0ehuaWmRfvbZZ8qvfOUrjrS0tADHcbj33nvNhw8fnrRpyLp166wMw6CsrMwzODgY8r0LN87ly5fbExISeIVCIebm5npaWlqk+fn53o6ODul3v/vdjPfee0+j0+kiqq6FlaCLosiLorgIgAFAOUVRJQCeArB9ov0oirodQJ8oilWTnYOiqB9SFFVJUVRlf39/OGERYkzR8rRZ1cRzWJeuSZRPPniOQXsEFLspdFjdeLNnINbhECZAEAGlhIWUje0fh0rKwhsgsy2zCZKgz00YtTSsN47RSKJ6g0tKSrynT5+uW7hwofupp55K37Ztm/7RRx/N2rt3b0tTU1Pdhg0bBjwez0i+JpPJRABgWRY8z4e80TzxxBPpK1eudDQ3N9e+//77530+Hw0Ad999d3Z+fn7hypUrc68+Hk3TkEqlI9NuNE0jEAhQ4gQzcRKJZORFhmHEQCAwKh5RFEFR1JgDPP/88ynJycn++vr6unPnztX5/UF50MMPP5yen59fmJ+fX3h1fAzDjDpfOPFR1OVw3G73qNiGjzscZyjGi/Nqrv45+P1+Kikpia+pqalbvXq1Y+fOncnf+ta3sscNNAQR6aVEUbQC+BTANwDMA1BNUVQrgon7aYqirl4ksQzAuktj3gZwM0VRb41z7N+IorhUFMWlSUlJkYRFiBGaRDkyC2a2QQtFAWkLtJDIWchUHDjp5RkjlU4KiCKY2dDWcRoQKQo6OQeW+WJe3xeFUoMWlW0WeGPothOvlEAQRQhE4TKr8AaEWeWZTwgPRVmyheLoCVUAFEcLyiXJUWnbWltbObVaLTz00EPmrVu39p45c0YBAKmpqQGbzUa///77k7oyaDQa3ul0jnw42O12xmAw+ADg1VdfHTHxeO+991obGhrqDh8+fD7c+G6++Wbnhx9+GOdwOGi73U5/+OGHutWrV4c1PVdaWurp7e2VHD58WAEAFouF9vv9sNlsjF6v9zMMg507dybwfPDv4uWXX+5qaGioa2hoqAs3vptuumno5MmTapPJxAYCAfzxj3+MX7VqlRMAEhIS/KdPn5bxPI99+/ZN+nPUarW80+kcSSzGizMcTCYTy/M8Nm3aZH3uuee6zp07F1HL80nnyimKSgLgF0XRSlGUHMBXAewQRTH5ijGtAJaKojiqtCeK4pMAnrw0ZhWAbaIobogkQMLspmhFOtrrzJMPnAISDSqwUhrdzTawEhpxKSowDAX3kB/WHhd8Hh6clIHP88VsBqJuceH7YGEq1OKtblJFn02opCzilRKYbG50WtwxjYWlgfmJSlS2zQ4dPGE0NrcfMu6L7zb1RYJRcLzyhjST80jnuO4IyhvSTLSCi0rKW1VVJX/yyScNNE2DZVlx586dbe+9915cYWFhkcFg8JWWlg5Ndoxbb73V8Ytf/EKfn59f+Oijj5qeeOKJnu9///vzXnrppdQVK1bYo4lrmOXLl7vuu+++wSVLlhQAwP3339+/bNkyd2Nj46Sr4mUymbh79+6Wf/qnf8r0eDy0TCYTjhw50rR169a+ioqKnD//+c+65cuXO+RyedQy6KysLP/27du7Vq5caRRFkbrllltsGzZssALAz372s65vfOMbuXq93p+fn+8eGhqasMJVXl7uZllWzMvLK7zvvvsGriXO1tZW7sEHH8wWBIECgGeffbYzkuuacGoAAC7JWf4HAINgxf1dURSfvWpMKy4l6BRFpQH4rSiKa68aswrBBP32yYJaunSpWFlZGcl1EGIEzwvY9S/H4bJN/2LRpCw1+tsdl5coU0C8XgGpnANoYLDTCT4ggJOy8DhnfipZYClcKFDgc+cQEmXBCuZ8ToJ55ya9t0aEqUiFt7qIDGw2cV22DrVdNhSnx+FU68w8sI5HslqKPoc3pjEQxuevj9wEY0rs1ygQgtTX16OgoAAAUFNT4youLh7Xcc764cXUoRPd+isXjFIcLShvSDPFrZ3XMwPhEr6AVFdXJ5aWlmZfvT0cF5ezABZPMib7iq+7AawNMeZTBOUxhC8QDEOjcFkaKj9snfZzDVm9oHA5P4cImLtdY8ZpEyWQKVlYe2eukilIaXyUzeBMR7Cy3Yrgubk0LeZN8bnEsXI+QozIjFfA6fWj0+KGyy/EPDkHAFEEaApE3jJLITr0uUvc2nk9mlWGvqHTfTre7uMYjcSvXJJsibZyTiBMBLGDIFwzBcv0qDzQekXmPD24bD4kZ2sw0OkAK6Hhc4XWgkmVLCgKM5age1KkOKjyo7l37Cyi3c/DlywB7RUgShgwg16AAugoZKieNClAUbCTBD2mxCk45CSpMOj0om3QBZWMhXnIE+uwRuh3elGercOpWWL1SBgNsVqc29AKTojGSpFAiBSSoBOuGU2CHFlFCWirmf57Vl+rHQxHAyKFtAVx8HkCsA+44XMHM960BXHoPm+FKi5kT4Ypx5yrwC6LGf7B0Elzfb8z2KGLAuAHOB2FH8njIO+MPKHbJThh8wSAqVXMECLE6vLDF+DROhicvXHMwjUP5/uGoJVzM1atlbA0pAwNjqUhYWhIWAoMTYOhKdAUQFPUpa8pUFSwwk9RFCgEXwOCC8ApUMG/FVHElRZRIsRRs2eX9sCwQcPo0cHveUFEv8OLdvPYWbZYQiroBAIhHEiCTpgSilakzUiCDgC8XwDvF9DdbAXD0UjOVkPkRfR3ONHdbIV+QRxMzVbEpyth7pq+bNY2X47/MZsRiEBL4OdFfKbkkV+sREZN6NhEiOgrVOGI24UMhRTFDuCsWoSrZ/ZUab/szHb5iNPrR1GaFoIogg8jWBHBpkaiiBH3F3H4X0EEL4qXkl4BggD4BRH+AA9vQICPF+ELCPAFhGDf6VmEhKFQlqVDVZgLZjmGgigior/pSCEJOoFACAeSoBOmhKziBCjjpBiyTv8nNMPRSM4KLrLyDPlharaNvEZRgM/lhz5XC5Zjpi1Bd2bJ8YbdGtUH+ZleO1rlHO7N0YDmAYXJA8rLQ5AxEGUMqg0sPu68pGW3uHAUAK5pDT5hqlFKZ/et08eL+LxjwiZ6Xwp8vIiqNgtKDVrQNIUOswsDzuCC9vlJSiglDDiGxul2K7RyDrnJSvTYvDC7fHD7xurQFmfEgWUodFnc4AURMo7B4JAX+amasF1zbK7Yd18mEAizn9n9KUOYM9AMjcJlevz9g9ZpP5fIB5NiigLkKg5IVcDSE5zGFkXA7fQHv6eAxAwlBjqmNkl3Z8jwhssWrBhGidXtR3cicKTfBjaRxp1KDX7bd8k6MSIjJsJMszBdg7YBojOaS1R3Bh/itXIWxhQVmnqdkHMMznUFn3xT1FL0Oryoags+1OSnqqGWsfAGBDT3OeH28ZBzDDosLqRqZNBr5ahqv5yQV7ZZUD5PB6vLD5PVA4d3fNkTqaDPbVwuF1NdXa1zOBycWq32l5aWWhQKBTG3J0w5JEEnTBmFy4NuLpM4d14zgiDCdN427usumw/6HC14XoBEzmIqRdu8msGbASfcU9Bs5P2Oy5Kg3w4RX/O5RC+xMZyT2NwBBHg3SgzaEe07MPb9bOgZ3YNlYboGNEWhutM2UoG/mlMXgwm7WsqgLDMObj+P+h7HmPshSdDnLocOHUo9efKkPhAIjNgsfvTRRxnXX3+9ac2aNTG1Wdy/f79aKpUKa9asGQKAioqK7Ntvv932wAMPTDi1E+44wsxDEnTClKHSyZC1MBGtZ2OfbJpaLifwyVlq9LWF1fRsUkSawq0JWrzdOYC8RCWuk8rRSws41BF7ez3C9JOqlcFKEqw5zZCPx9nO8R/wQzFcaQ8Hh5dHVXuwEk8hWI23e/zotgbXkJDfn7nJoUOHUo8dOzamUVEgEKCHt8cySf/444/VKpWKH07QCXMf0jOcMKUUrUiLdQhjGLJ6wbDU5APDgLUFkNrjx1K9FjcLUuhrhzDfRaE4WY1snQIK0iHwC4tKyoKmgA5zbDuFEuYOIoLV+B6bBwV6NcrnxYOlp+ZeRJg5XC4Xc/LkSf1EY06ePKl3u91R5VR2u51etWpVbl5eXuGCBQuKXnvtNd2+ffvUBQUFhUajsXD9+vXZbrebAoD09PSFJpOJBYAjR44oysvL8xobGyW7du1KeuWVV1Ly8/MLDx48qAKAw4cPqxYvXpxvMBgWvv766+O2uT906JC6rKwsLzs7u/h///d/tQDQ2NgoKSsryyssLCwoLCwsOHTokBIAvvnNb85766234ob3Xbdu3bzdu3dro7luwsSQBJ0wpWQWJUAVPzMWh+EyZPMhZd7U3T+4AR9W1/uguhBM1DQtLtzaFMD6iyJWp8ZNsjdhrlKYphmpghIIkSCIQL3JgVMXzbhA1i/MOaqrq3VXylpCEQgE6DNnzoybBE/E3r17Nampqf7Gxsa65ubm2rvuusv+ox/9aN4777zT0tTUVBcIBPDCCy8kjbd/Xl6eb+PGjf2bN2/ubWhoqPv617/uBIDe3l6usrKyYd++fc1PP/30mOr/MB0dHdJTp041vv/++81bt27NcrlcVFpaWuDo0aNNdXV19e+8886FRx55JBMAfvCDH/S/8cYbCQAwODjIVFVVqe65557IpqQIYUESdMKUQtMUCpfNviq6Y/DaEiuRBj40svhgAYOuIhXcmXLw6rHVclIb+2Ii5xiYbKRyTrh2bKRR0ZzD4XBw4YxzOp1hjbuaJUuWuI8eParZsmVL+sGDB1VNTU0Sg8HgLSkp8QLApk2bBj/77DN1pMddt26dlWEYlJWVeQYHB8eNraKiwswwDBYuXOjNyMjwnjlzRubz+aj77rsv+1IFP6elpUUGALfddpuzra1N1tXVxf7ud7+Lv+222ywcF9VlEyaBaNAJU07hsjT8/YNWiDE2i47XKyFVshAFgKIBUNEn6s5sBWr7gos66+AEAGQnyrE2QQ63jIafATgBGOBnX9MawrWz0KDFqYtknQHh2rG5/RBFERRFHufnCmq1OqynKpVKFdXTV0lJiff06dN1e/bs0T711FPpq1evHnfRA8MwoiAEHcQmk9TIZLKRD2Hx0mrlhx9+OP3QoUNaAGhoaKgDMOZ3kaIoPP/88ynJycn+PXv2XBQEAXK5vGz49XvuuWfwt7/9bfyePXvif//7Oxkb+gAAIABJREFU37dGer2E8CAVdMKUo4yTYl5JYqzDgCCICPgEBAJBxxVlnATRfiYKIf5SWi1u7LSa8XrPAN7qGsDrpgH8rZt4TxMIhPEJCCKGQnisE2YvpaWlFpZlJ/TVZVlWWLRoUVROKK2trZxarRYeeugh89atW3tPnjyp6urqktTU1EgBYNeuXQkrVqxwAIDBYPAdO3ZMAQDvvvvuiKRGrVbzDodj0kVQL7/8cldDQ0PdcHIOAHv37tXxPI/a2lppR0eHtLS01GOz2Ri9Xu9nGAY7d+5M4PnLv7ObN28eePXVV1MAYOnSpUT3N02QCjphWii6KQ0XzvTHNAZr79gW30mZagx0OiBGaGGu6vUCZP3nl5YAH73nPYFwNTa3H6pZ3uyKcBmFQsFff/31plAuLsNcf/31JrlcHtWNoqqqSv7kk08aaJoGy7Lizp072ywWC7N+/focnudRWlrq2rZtWz8AbN++vXvz5s3ZO3bs8JeVlY0saKioqLDefffdOQcOHIh78cUX2yM5f25urre8vDxvcHCQe/HFF9sUCoW4devWvoqKipw///nPuuXLlzuuvLaMjIxATk6O54477iAVqWmEEqfbtDoKli5dKlZWVsY6DMI1IAoi3nr6b7D3zz7dbmKGCj43D5fdC1EUwftFaJNlkMg4iKIIiZRFb7sdvG/0vfYvuTQayQKvLyU5SUq09JP3njA1fPhPK1CYpol1GAQA9fX1KCgoAADU1NS4iouL68cbG8oHnWVZYTb4oM8kDoeDLiwsLDxz5kx9QkICmQ66RqqrqxNLS0uzr95OHuEJ0wJFUyhakYYTe1tiHcoYBjqCGnKVTgpNogy2fjfsgx6odYB9IDhbF8o7PVcuQ+MUNj0izB10CgmmsuEV4cuN1R262RFhdrNmzZqe5cuX9505c0bndDo5lUrlX7RokSXayvlc5M9//rN6y5Yt2Vu2bOklyfn0QhJ0wrRRcKMep/5yEXxgdt67nBYvnJZgB8GkLDWc5stSOp4XkZYbh+7zl2fwyJouAoEwFdhJs6I5i1wuF2644YbByUd+MfnmN7/p+OY3v3ku1nF8GSCLRAnThlwlQU7ZuNats4r+NgfcjssfmoOdTvS02qBJkiMuRQ4AqHHMPrkOYWZw+0mhiDB1WInVIoFAmASSoBOmleKbDLEOIWqEgAh7vxsKtQRchgKtlrGLTgkEAiFSbKSCTiAQJoEk6IRpJXW+BgnpyliHcU30dzghV0mIicuXGCVx3CBMISRBJxAIk0ESdMK0QlEUim8a15lqTuD38vB1OPHPcSakaSSxDocQC2ah2xVh7mIlCfqcxeVyMSdOnEj861//qj9x4kSiy+UitRvCtEDKQoRpx3h9Ko7vbYHfOzd1vCodB4XyOKyfH8WdCi3OLt6Io92kY+iXAYoCitM0ONUaVf8RAiEkpII+Nwlls/jRRx9lzAabxf3796ulUqmwZs2aIQCoqKjIvv32220PPPBATG9ex48fl3d0dEjuvfdeWyzjmIuQCjph2pHIWBjLU2IdRlTEJXNwDrwBc1ew6RrtsqH02Mu4P6EP+YlSZMVJkKzioJOz0MgYKCQMJAwFjqHA0hQYmgJN3F/mLNdl6XCua9yu2wRCVNjIItE5x6FDh1KPHTuWfmVyDgCBQIA+duxY+qFDh1JjFRsAfPzxx+qjR4+qYhlDKCorKxUffPCBNtZxzEVIBZ0wIxSvTEft0e5YhxERCeks+s7/Gn5PMEFLzMzGQHsrKABxlXuwJsLjiQAoigZoGhRNAxQDUBREUMF/KQoUBYig4ci7Cf9jNWBtmoD51X+ESDM4nP8d1PR7p/oyCSFYlBEHjz9AKueEaYFU0OcWLpeLOXnypH6iMSdPntQvX768LxpPdLvdTq9bt26+yWSSCIJAPf74493JycmBn/zkJxnDnUR37drVJpfLxfT09IWVlZX1er0+cOTIEcW2bdsy3nzzzYu7du1KomlafPfddxOGO4kePnxY9dJLL6X09/dz//qv/9oZqpre0dHBfu9738tqb2+XAsB///d/t61Zs2bomWeeSdm9e3ciANx///3927dv72tsbJTcfvvtC5qbm2sBYPv27SlOp5P5j//4j+7y8vK8srIy52effaZxOBzMK6+80rpq1aqhf/u3f0vzeDx0fn6+6tFHHzU999xz6SdOnGhIS0sL8DyPefPmFZ88ebJBr9eTaemrIBV0woyQaFAjdf7c6ZyXnEWhp+G/RpJzAJAqr22xKwUAogDwAYh+H0SfG6LXBXiHAI8TlNsBuBygXDb0K9IgY2n08DJQTjNoez/kDNFBzwRLs3Q402FFQ48z1qEQvqCQBH1uUV1drbu6cn41gUCAPnPmjC6a4+/du1eTmprqb2xsrGtubq6966677D/60Y/mvfPOOy1NTU11gUAAL7zwwriexXl5eb6NGzf2b968ubehoaHu61//uhMAent7ucrKyoZ9+/Y1P/300yEXg23evDlzxYoVjsbGxrra2tq6JUuWeI4ePar4wx/+kFBVVVVfWVlZv2vXrqRjx47JJ7uOQCBAnTt3rn7Hjh0dzz77bJpMJhOffPLJ7jvuuMPS0NBQ94Mf/MBy9913D/72t7+NB4B9+/ZpCgoK3CQ5Dw1J0AkzxlxZLJo6L4D26v8EHxhdrfY4HWAl0hmJIefYq/h+9x9wQ82ukW0cRRL06SY3WYUzHaRqTpherC7SSXQu4XA4uHDGOZ3OsMZdzZIlS9xHjx7VbNmyJf3gwYOqpqYmicFg8JaUlHgBYNOmTYOfffaZOtLjrlu3zsowDMrKyjyDg4MhYzt+/Lj6scce6wcAlmWRkJDAf/rpp6q1a9daNRqNoNVqhdtuu83yySefTHr+9evXWwDgxhtvHOrs7AzpqLBly5aBt99+OwEAfv/73ydu2rRpINLr+rJAEnTCjJFTlgypcnarqlLnOdB6+qVgpfsqBjvaoUpIhC5tZrzdqSELaOflZHFR219hTJiZB4QvI0pJ0Ixhlja+JXyBcHgDEATywD1XUKvVYU15qFSqqKZGSkpKvKdPn65buHCh+6mnnkrfs2dP3HhjGYYRBSF4k3K73RPmcDKZbOSXTLzkRPXwww+n5+fnF+bn5xeOt584jmsVy7Ij5wYAj8cz6vzD52NZFjzPh1x9lZub609MTAz85S9/UX/++efK9evXk8Wj40ASdMKMwXIMCm6YUMYXOyggOdOE1tOvTTjMauqCpbsThoLiGQrsMkxXA7527lU87j0AnXzsg45ayqIsU4fybB0SlMQOMhLilRyK0rU430dkLYTpRxQBh4fM6s8VSktLLSzLTvjozrKssGjRoqim31pbWzm1Wi089NBD5q1bt/aePHlS1dXVJampqZECwK5duxJWrFjhAACDweA7duyYAgDefffdEUmNWq3mHQ7HpJaPL7/8cldDQ0NdQ0NDHQAsW7bMMSyfCQQCMJvN9M033+z88MMP4xwOB2232+kPP/xQt3r1aofBYAiYzWa2p6eHcbvd1P/93/9NuvhTo9HwTqdzVK75ve99r//73//+vHXr1plZdnYX7WIJSdAJM0rRitjLXORqFlLJB0jO7EVSJgOpgkFCShPaq/837GN0NdYhNTdvGqMMjWp+Ed5I+AYs7gAoCshPVWNxZhyMKSpkJSpQ1W7BqVYL5BJizRsJXr+AUxfNsQ6D8CXC6iYyl7mCQqHgr7/+etNEY66//npTNAtEAaCqqkq+aNGigvz8/MIdO3bon3/++a5XXnmldf369TlGo7GQpmls27atHwC2b9/e/fjjj2eWlZXlMczlhUkVFRXWDz74IC4/P7/w4MGDYbu5/PrXv24/fPiw2mg0FhYXFxeePn1avnz5ctd99903uGTJkoKysrKC+++/v3/ZsmVuqVQqPvroo6by8vKCW265JTc3N9cz2fFvvfVWR1NTkzw/P7/wtdde0wHAt7/9bZvL5WJ++MMfDkbz8/qyQI03lRFLli5dKlZWVsY6DMI0se/Fz9HZEDudb0q2gLbPX5ySY6UZC9DdVD8lxwoHVVE5/iBbjlStHKfbLfDzIrRyFjb36GocQ1PgyRR6WEhYGhKagtM3N336CXOTv/y/ZSgxjKtkIMwQ9fX1KCgoAADU1NS4iouLx72hh/JBZ1lWmA0+6HOJI0eOKB555JGMqqqqxljHMhuorq5OLC0tzb56O5lbIMw4RSvSY5qgD1mnTsc92NUBmUoFj3P6pRGcTAY/I0e3zYM2s3tk+9XJOQBIGBpugSSckxGvlCBeKSHSFsKMYyVe6HOONWvW9CxfvrzvzJkzOqfTyalUKv+iRYss0VbOv4z8y7/8S+obb7yR9Prrr1+MdSyzHZKgE2aceaWJkKs5uB2x+YByWv1Inr8MfReOXfOxvENOpMzPhcd5fgoim+RchavwK3M2EIabS26yEjRNocPsgnmIJALDpGpkSNFI0W52YUGKGpWtZpiHiNSAMPMQq8W5iVwuF2644QYizYiSn//85z0///nPyWxDGBANOmHGYVgaBTemxTQGRdzULfLsvXD+mheNUvTkf4of+dKDvefD4FyXHdUdNkAMyl0IQbISFKjutMHi8uPURTOICogQK0iCTiAQJoIk6ISYULh8ahL0lGwrUrItUMZFZj8r8BFbyk5IZ30tkjKzo9o3wZAJTUISVPEJE44LiJEn2maXnzi6XEFlmwU5SdfWcIpAmApIgk4gECaCSFwIMUGbJEdGgQ4d9dFr0ePTOLR9/nsAAEUxSMu/FSJVBLNp8g++/g4BCRlLMNhxOurzj0aE02KGMk6HIWv41xSXqofDPACfy4W41DRIlSp4h0Lroe8Wz6E5Pgt7zBMn8gDA0kBphg4MDfgDIvoc3kn3+aLCMRQWZcTB7ecxC9fEE76kkASdQCBMBKmgE2LGtVousmznyNeiyKOrfj+663YgOTMob6NpCgn6JvjsLyMhtQEUDSjjOKTO8yFBfwEK7dQ2/XE77OBk8rC7jaoTEuF1ueBzuQAA1p5uqBOSwHChZwM8zZ8jQQyOna+T4iHfJ9gSOIo0jWSkyc4wSzLjUdVmwamLFrj8PL6sKhc5x0DOMajtsqGmy47abjt4gaznIsQe0k10buL3W5j29t8nNp//d317++8T/X4L8bQlTAukgk6IGdmliZBrJHDbo/ugEvz2kNs7zr6DrCX/DJf1FLrqjgIAuuo/BMN+BPegF4NXrB1Pyp6P/tYLUZ0/FNaebqTkLEBvS/OE41S6eIiiCLd9dBO1gfaLSM01gmE5iKKA7sbLjl+KVANetGRAK2Nx2+nLNpEVHTU4v2wzDnRfzsI9gcsOLo09jmu9rDlJbrIKDAU09o6ekWjoIY4thNhDKuhzj/Pnd6R2dO7SC8LlDpotF36ZkWHYaMrNfSKmCx/379+vlkqlwpo1a4YAoKKiIvv222+3PfDAAxNO6f74xz9OU6lU/LPPPts7M5ESwoUk6ISYwTA0Cm7U4/TBtqj2F4TQiX16fgHaz/wXBH60zSAfGCvzsHR3ISEjC4Md0cUQit6WZmQUlaCj9mzI1/UL8mE634jx9BY955sAikKasQDJ2Tmw9HTj8IJ74QeFVEqCde5To8aLANS8E8BlXb1zGrsULi1NgVvLghIpyFw8hgbcqG+zTtv5omXI64fJ9uWV9hBmNyRBn1ucP78jta39N2OmfQXBQw9vj2WS/vHHH6tVKhU/nKAT5j5E4kKIKQlp0S/Y83tDV9D9Xs+Y5Hw8Aj4vPA47GG5qF1La+nuRZswfs10Zp5swOR+Gphk4zQMwm7qgyV+MKqccZ50yGNUCpM0nRo2tXfaPeLf3cnK+JDMOFwam7x7t0XCokgOVChGueUoo8nWT7zRDaOUcCvUaxCs49H+JdfeE2Q/xQZ87+P0WpqNzl36iMR2du/R+vy2qnMput9OrVq3KzcvLK1ywYEHRa6+9ptu3b5+6oKCg0Gg0Fq5fvz7b7XZTAJCenr7QZDKxQLDhT3l5eV5jY6Nk165dSa+88krKlZ1EDx8+rFq8eHG+wWBY+Prrr096o/7lL3+ZWFxcXJCXl1f4ta99LcfhcJAcMYaQHz4hpijjoteBu2zdIbdbeyMrYgxZLUiZNz/qOELhNA/CdL4ZqTnGkW3KOB1YqXTS5FwiVyDeYIC9vw8BrweuC7W4KzH4MJIojpVn5HUfH/V9YAa9Azu9fgRr+LGnUK+GCBF1JjvMLj8CRGpOmMUka2SxDoEQJibTn3RXylpCIQge2tSzN6pqxd69ezWpqan+xsbGuubm5tq77rrL/qMf/WjeO++809LU1FQXCATwwgsvJI23f15enm/jxo39mzdv7m1oaKj7+te/7gSA3t5errKysmHfvn3NTz/99KSLvr7zne9Yampq6hsbG+vy8vLcL730UmI010OYGojEhRBT1AnRf0ixXOh9ZarxnVDGo7upAYaCInTW10Ydz5UoNFo4zYPoaWlCWl4hes43gWZY2CZ5eFDq4sFKJBhoax3Z5rbbUNj+MTJFFoHjHWP2CcjjkMZJ0H1Jy18Y6ESWXob3TZFZTwLAujQ/MhoOAqIIy4qv4f3k+QA1OgU/e+m7XLkU591eLOAjP890IIiAPURXVQJhNlJq0MY6BEKYeH19Yd3kfN7wxl3NkiVL3E899VTGli1b0r/xjW/YtFotbzAYvCUlJV4A2LRp0+CvfvWrZAB9kRx33bp1VoZhUFZW5hkcHJw0tqqqKvn27dvTHQ4HMzQ0xKxcudI22T6E6YMk6ISYooqTgqIpiFFUfWkmtCxFrtZMmgiHwuf2RLzPeKjiE+A0B5vNdTfWIS2vEAIfgGOwf9x9dPo0eFyukLHbek1IypqHAZqBKIyW78jrPkEFPoEg10BUaiH6VVDGpSNFXYjeq7q1Lk6RYB7tGEm4RQAUhhNwCskDjaAHg+44yp4W9OtDzyxIKEDNXiooXTUjoFBwSExSQIQ4ktmPnE+8YoMIBHgBvT1TI8dp6XeifF48TreZSfWcMOspMcTFOgRCmEglyWHpkSTS8MZdTUlJiff06dN1e/bs0T711FPpq1evDq3fBMAwjChccqJyu90TVvVlMtnIzXn43vvwww+nHzp0SAsADQ0NdVeO/+EPfzjvvffeO3/DDTe4X3rppYTDhw9PbcMQQkSQBJ0QU2iGhipOCoc58uTYaQ69sFPgeSg0WrjskT38u51T53bCXqVpt/aaoE1OQXp+EboaRlfpZSo15GoNHOZBBLzj/xz62y4izZiP7qaGkK/TbjvgDt7X2c56VKS1I6BKQl9iHvqhQrMDyBP7kHT8fyeNX5TKYJ43VkM/TLFKgdOOoOUj+NEJem5xIk7pwlPP6TkW2D81CbqfF3HqohkqKYv0ODl4UcD5PrJeijA7IRX0uYNef6el5cIvMyaSudC0TNCn3hVVY4/W1lYuOTk58NBDD5nVarXwm9/8Jqmrq0tSU1MjLS4u9u7atSthxYoVDgAwGAy+Y8eOKe655x77u+++OyKpUavVvN1un9Ty8eWXX+4C0BXqNZfLRWdmZvq9Xi/19ttvx+v1erJQIoaQBJ0Qc9QJsjEJOieloYpnIJF5AcEM3u8AI8lGfzsNQRCROs+L1tOhiwy2vh7w/silDo6BPsjVGrgd4xYvwsbncY/63mW1wHWpgdGVSXp6fhF6L5yHy26bMDkfJijFKUZnfc2kY5nuJjBoQkbTMWQAWBJB/Pw8I3bHZYR8rVApw+fDyTmAcwoRCXdkg6MABhQ6RQHwhffzp6ipN2h3egNo7A0+bMUrOJjJYjzCLEOvlREN+hyC43R8hmGjKZSLyzAZho0mjtNGNXdXVVUlf/LJJw00TYNlWXHnzp1tFouFWb9+fQ7P8ygtLXVt27atHwC2b9/evXnz5uwdO3b4y8rKRioQFRUV1rvvvjvnwIEDcS+++GJ7NHH85Cc/6S4vLy9IT0/3FRQUuJxOJ/F4jyGUOAtb6y1dulSsrKyMdRiEGeKjN+rQ8LceaBI5SKTNsHT9HUOWsVprAFDoDEjKWo226t2AOP69MD49A3K1BhRFwedxo+9iS1ixaJNTYeu7NqcsRiIBBAF8YGySKldrwMlkUGjjwHAcuqLUvKflFaK7sQ6gKFAUBd2lLqS83we/1wuvawgepxMCH50mW6RZtH7nH7FXmYQrf8plGgXa3D4MRPEAFAqDhMPA+61TcqxQaOUcjCkqVLZaZslSVgIB+FpRCl69f2mswyAAqK+vR0FBAQCgpqbGVVxcXD/e2FA+6DQtE2aDDzph7lJdXZ1YWlqaffV2UkEnxBxdmhJJGQy66/8LvH/iKrLL0ok2y5uTHtPcNTrBT8zMxkB766T78VEmtFcSl6zHYGdo+Y3b4YAqPiHodR4lNMNCFHjEpegR8PswZLXC3N0ZciwrlSEpIws0ywCgIPA8+IAfLpsVnqEhJObm4bOv/AM01gHQAo8qQx6soOADBQkAwT9a7+4VxClLzmcCm9uPv7daYExRgQLQaXFjyBeeBSeBMF0Q/fncJDf3iZ6srM19pp69Op+3j5NIk/361Lss0VbOCYSJIAk6IeYkpvE4XPsSBH76fKulivD81lW6eDgHB67pXAw70aygCJfNdk1SmtTcBaM6jE5EwOuB6Xwj9MZ8mK7SrtMMi57aanSsXo9K7pIe1n9p9eYMMfUCl8ssytCCF0TUdtuhlLKQMDSsLj9J0Akxp5Qk6HMWjtMKmRkPDMY6DsIXH5KgE2KOKl4yrck5cIV7yAQotHGw9piu+VyT6aqHrGYkZGRFlaCn5hjDTs6BoJsMK5WCoigwnAS8/3L31WH5S/m5Y6gsWBZxLJFyg1Z5pWUMAEAWEDG+r010xCs5ZCUo8Xl7sLtpVrxi5GsCYTawkCwQJRAIk0ASdELMUSeO239hSqBoGu4wHF10qWnoaqybdNzkJ5y8LjzY0Yak7Pnob70Q0aEZSfg2uyM6dQBWU+imTgCgPHwANxVdjyPC5LeDa6l4X3B70XvV4tHMwNTU0OUcg4XpWvQ5PFDLuFEJeZvZNcGeBMLMMj9RCa18dvQOIBAIsxfSSZQQcziJFDQzfc+KCm0cLKaQrlKj8PumqIpPTf5npTfmw+tyRXzdpqZGJGZlTzhGolAgvaBoJDkPh5LKT8BOp94EAB0ivRen4Jwl6VoYdHKcajWj3exCbTfprUGYvZSQ6jmBQAgDUkEnzArECRxZrhWXLbyELTBFCTpFT5x1SpUqmLs64B0amtDXPBQCH4C9rw/J83JGnGn0C/IQ8Pshkcrg93rhNA9E7A4jP3UY64rKsFcaP+G4a8mnQ/1YolW7L8mMg8fPo8vqxtmuy+9vFP2uCIQZhSwQndv4/RbGZPqTzuvr46SSZL9ef6eF43RkYQthyiEJOmFWIArTl6Drc40QhPDun6m5Rvjcbgh84JKWPGhjCIoCK5GAD/hBgRqxNwQw8vrw17JJFqQmGDJGdOTdTQ0hmxdNhM/tQt/FFijjdEgwZKKzvjZqO8Urmfc/L+Lmzf8fPhZCd2gFwlLvjL9viG3R5NMMTUEUgTrT1DWWIhBmitIMkqDPVULZLLZc+GXGbLBZ3L9/v1oqlQpr1qwZAoCKiors22+/3fbAAw9E1TxpMl566aWEdevW2bOzs0mjiWmCJOiEmDP9XvziNdkaDiNTa+AJY2FnmnH8DpwJGVljFnl2NdSG3XzoSoasFsSl6qckOQcAWhCw5PVfovMHT6HJN/UPTFNVQU/VyHC+jyTnhLkHS1MoStPEOgxCFJw/vyM1VKMiQfDQw9tjmaR//PHHapVKxQ8n6NPNW2+9lbho0SI3SdCnD6JBJ8Sc6ZS3ABScFvPUHCnM8vFESadcrQ65vbO+Bml5hRHFo9TFT/nDDeUews01J0K+tlSjwAVX+DIgGsBXtEoUKGUoVMrQ5x39IPEVrRJJKikW3mRA6XIDltyQjqXlabiuTI/5Kapxj9tldSNPr8GSVZkoW52JgpLpXWRMIEwVxhQ1ZBxpzjjX8PstTEfnLv1EYzo6d+n9fltUOZXdbqdXrVqVm5eXV7hgwYKi1157Tbdv3z51QUFBodFoLFy/fn222+2mACA9PX2hyWRiAeDIkSOK8vLyvMbGRsmuXbuSXnnllZT8/PzCgwcPqgDg8OHDqsWLF+cbDIaFr7/+um74fD/96U9TiouLC4xGY+EjjzySNrz9q1/9ak5RUVFBbm5u0S9+8YtEAAgEAqioqMhesGBBkdFoLPzZz36W/Prrr+tqamoUGzdunJ+fn1/odDqneQXTlxNSQSfEnOmUt6TnF0YkH5kIt90GTioFKBoURSE+zYCelrGV+f7WC1DpEkZkMMMSGIqi4HE6wUqkIfXu3U31o7TlE0HRNJTaOPReaEFCeiYGu6Lq7BwSxYmPccPS1Qjg8sOGxc/jrMMNXwQPBEkSFn+zjV/MEQBUuz2A/MqtQVnRcq8CF3qd4+7bOuhCZ54CAFCeoQbOTrVZI4Ew9RB5y9zEZPqT7kpZSygEwUObevbqovFI37t3ryY1NdX/6aefngeAwcFBpqioqOivf/1rY0lJiffOO+/MfuGFF5K2b9/eF2r/vLw838aNG/tVKhX/7LPP9gLAa6+9ltjb28tVVlY2nDlzRnbnnXfmPvDAA5a9e/dqzp8/Lzt79my9KIr46le/mnvgwAHVrbfe6ty9e3drSkoK73Q6qcWLFxdu2LDB0tzcLDWZTFxzc3MtAAwMDDCJiYn8r3/96+Rf/OIXHTfddBOxyZomSAWdEHPEaVzZZ+u9dl/zK/F7vfB73PC5XXBaQ1fmAz4fnJZBOM0DcAz2wz7QB3t/L0QAA+2tSMlZEPrgoghzdxd0+jGzqGNIzTWir/UCeL8PQzYz1AlTV0Vm3EOQOaz4u92Fykv/tbi9ESXnANDrCyB+nGphupSDLTDBuoBJTkVfMZt9dSZGAAAgAElEQVQxFU4wBMJMsJgk6HMSr68vLF9Mnze8cVezZMkS99GjRzVbtmxJP3jwoKqpqUliMBi8JSUlXgDYtGnT4GeffRZ6+nUC1q1bZ2UYBmVlZZ7BwUEOAA4ePKg5cuSIprCwsLCoqKiwpaVF1tDQIAOAHTt2pOTl5RWWlZUV9PT0cLW1tbL8/HxvR0eH9Lvf/W7Ge++9p9HpyILYmYIk6ISYM10SF1V8wpTJW65GnZAYUcdRiqaD1XcAfReaIVeH1qEGvB54XENQxulCvg4E/c2v7ArqcToBKugOM1UseefXKOGuPfMNdYRUCQuGotA45Bl3v8mkO8wVgnaeJOiEOcKiTJKgz0WkkuSwdNYSaXjjrqakpMR7+vTpuoULF7qfeuqp9D179oz7i8IwjChcmnV2u90T5nAymWzkRjp8TxVFEVu3bjU1NDTUNTQ01LW3t9c88sgjA/v371cfPnxYXVlZ2dDY2FhXUFDgdrvddFJSEl9TU1O3evVqx86dO5O/9a1vZUdzjYTIIQk6YVrwezyw9fXC1tcDW18PrL2X/7P19cIxOIAhqwVuhx3eocsyiJQcI3T6tAmOHD40M31aT7kmMi/jxMxsDHa0AQhW4ePTM8Yd67ZZwUqlkMjlY15LyysI6W/uGOiHShcPhp2aBii0uR9rfvVTbLB3Q8tEd5uQUFRI28NECYt2j2/sC5cwyqXoNo0vbwEA+oqQBJKgE+YAKimLnKSpe4gmzBx6/Z0WmpZNWEmiaZmgT70rKseU1tZWTq1WCw899JB569atvSdPnlR1dXVJampqpACwa9euhBUrVjgAwGAw+I4dO6YAgHfffXekkqNWq3mHwzHph96tt95qf/PNNxNttqBe/uLFi1xXVxdrtVoZrVbLq9Vq4fPPP5dVV1crAcBkMrE8z2PTpk3W5557ruvcuXMKAFCpVLzNZiMLKqYRokEnTAstVSfxwUsvhHxNlZAIURDgcTjAB4IFh5QcIyzdnehtaQLDSSBXayDXaEHR9EhiGykCPz0zcQzLhqUTvxLpVcl2d1M9NEnJsPeHlBTC1tuD5Ox5GOhoH7kOpS5+ws6jg53tSM01XrNjDZ+WiUBSKg7ftA7VfgB8dDMciRIW3d6xBSVqEjf1OI6FZRIv+SslLmS+lTAXWJwZN2rmhzB34Dgdn2HYaArl4jJMhmGjieO0Ud0sq6qq5E8++aSBpmmwLCvu3LmzzWKxMOvXr8/heR6lpaWubdu29QPA9u3buzdv3py9Y8cOf1lZ2Uh1q6Kiwnr33XfnHDhwIO7FF18cd1HSXXfdZa+trZVdd911+QCgUCiE3bt3X6yoqLD95je/STIajYU5OTme0tLSISD48PDggw9mC0KwFPLss892AsDGjRsHHn744azHHntMqKysrFepVKQLxRRDTb/FXeQsXbpUrKysjHUYhGug9vBHOLjzP0O+dmViykqkkKlU8Hs88LouV9Jphh2xD4xPM0woeRBFAdaey1pziVwBmUoFn8cTli1ipEgVylGxhkOasQDdTaPtFVNzjCEXmY4ak2tET0szVLp4ABSc5sllNZH6qg8jAggULQHd2wXIlehcdTsOaFLhiDJBT5dy6AqRoJeo5DjrdIfcR8PQoCkgr3EIriE/Boo14AQKAQoQIEKkKIgQIbI0+i9N8xZJJWj5y8WoYiQQZoqHVuXg8a+Pb8FKiA319fUoKCgAANTU1LiKi4vrxxsbygedpmXCbPBBJ8xdqqurE0tLS7Ov3k4q6IRpYbgyfjWcTD6qahzweeE0j3U0GU7ORzptUhQ0iUljKs7qxCQ4BvpHuZ+oExIx2NkOuVqDzOJStNdUT9VlAQBYiSSiBJ2iaVh6usds72lpQsr8XPReOD/uvj3nm5BdWobeC81wh/mw0dVQi/SCYnRF6KtOAeBqT498n/XmS/hBSjq8uQXg+kyARIq6FbeijlMhETyK+juRUH8agbgEUDwPnpOgJ8uIenUibOL4XUcnqiEWquT4m20IboMCnACYaBGgr3w4C35dopBCEeDRNoFUhkCYTZQYIpPFEWYfublP9GRlbe4z9ezV+bx9nESa7Nen3mWJtnJOIEwESdAJ0wIfCN08R5eaCpfdDqd5cieqlJwF6G5uDH4jilCHSNCHcQwOQKdPB0VR8HuDCb/bYR/3QeFakMjlGLKGLzVkJRK47baQr7lsVjAsN26cqTkL0NVQM3JN4dLVUDslchemtwuK3q6R70trT6P0qjHSK75WA1gAgE9MgeOWdXhNlzX2oGHM8p+VTjyzd9bpBgXgOq0CvJuIXAizH2Kx+MWA47RCNFaKBEKkkEWihGlBHEf/zcmV0CSObwnIyWQYzuAYlgMuSVsYTgKfa3y7VbfdBoupC+buTtj7e6MPPAykysjcrqQK5bivOQYHkDI/N+RrhoJi9F5siTg5BwCIIgbaWxE3RQtuI4UZ6EX64Q9CvjbRTScQgeRORFDPLuFnn0yPQLiSJLUUqRpZrMMgEAhzCJKgE6aHEF03JXI5TE31uLqESrMs5GoN9Ll5kKnUoGgKKl08TM2XrQRT5+eiv2126IwZNrKJJ2Vc/ISvdzfVw1BQPGpbRlEJOutrrqmJU8DnQ8DrhVQ5/gPCdEJRoW8vEy0SjXQNnZsX4GXIwjvC7KbUoA27EzGBQCAAJEEnTBuXP4zS84sAAD63GwLPw2EeRMr8XCRnz4cyTgchEIDbYYfpfCMcA/0QBQFOi3l0cjqLPtwGOiNzlQnH7rGzvgZpxuACsgRDJjpqz0YV29U4zYPQJKUgLF3JVDPOKYUJuhB1eyKTJDkDPFQSBguXpCI5RQmNRhLR/gTCTFBqIPIWAoEQGUSDTpgWqCtKoVfrrx0DfXAMhNaSjz0ODZphxq0+TWbZR9E0UnONoCg6eAzq0j6Xjhc8blAsEST4NSuRIOALLkAUBQEiREAMSnB8bhdohrmssxfFS0qcy/8CACeRwudxw2W3hnWtPS3NiEvRQxGnw2DnuC5ZEdPfegGJmdmwdHeF1LqnFxQj4PWM/BRE8dL/qOA1B69JgChe+lmJIoaHnLzlLlwEC54CeNAQKEAABR4UPHTo5/8zDjcKlTJcdHvhvsIoPU8pm7B5USgueny4CB/Kc9VwpkmQT3HoP26CxemD0xt6HQSBMNOUEP35FwaLP8C822PW9XoDXIqU9d+TGm/RcSxZCEOYckiCTpgWRiXOUVa/U3IWoLelGbwgoHMcR5LJ1MciL0S1UHI8C8TJXFeuJL2gOCJZjsDzsPaawIVoUHStDLS3hrR6BACIYtjXdDWZZ47hLzesQ6RCnLohD5ZqFGj3+NDnCybSWjb6Cb0erx86loWPo9G8VAeIInJ4GqlDArw9bjS0WxEI1TWJQJgBStKJg8sXgX9t6U79XWe/3iOIIzerf7tgynjQkGT6aU7arLBZ/PGPf5ymUqn4Z599dnoXYxGmHZKgE6aFKyvow1VsmmZCJ4jjEUY+NdPKl0h0pEIgAIlCMeHi1hBngNXUNfmwKOhuqg/pke5xOqI+prT6FO5Yugr7OE3E+1baXUjkGOilHExeP07ZXJgnl6DV7QvnrR9DPMfAFuCxSC0HDQoMBXjigc+1FKRGBYxeClqXAMEdgN8bgBAQ4ffzsDv9MFlD+7ITCNdKVoICOiWRXs11/rWlO/VX7X1jGhV5BJEe3j7TSbogCBBFEcw0ds0mxA6iQSdME8FEVp+bB5lSBYblwvbxnhWMm4eHn6Cbmhvgc7kQl6pHen4R9AvyodBOPNUdp9dH59oSJkGP9KJR2/hr7Lia+/YrSOWiu5UM+HlIKArDHy8X3T4UqeTQS7iIjtPu8ePvdhe0LIPGIQ9OO1z4u90FEYAAwE0BZ2UijsZTOJbO4dR8OSqNClQXqXHx+njkrTQgWSOd7DQEQsSUEP35nMfiDzC/6+zXTzTmd539eqs/ENWNcMuWLen//u//PmJv9uMf/zjt6aefTvnpT3+aUlxcXGA0GgsfeeSRNABobGyUzJ8/v2jDhg2ZRUVFhS0tLZInnngiNTs7u/jGG280Njc3j9zIysvL844cOaIAAJPJxKanpy8EAIfDQa9du3a+0WgsvO222+aXlJTkD4979dVX441GY+GCBQuKtmzZkg4AgUAAFRUV2QsWLCgyGo2FP/vZz5KjuU5CZJAEnTA90BQYloPXNYSuhlp0NdTCEnFlOJw66jSV0Keww661x4SuhlqYmhvgslmhik9AmjEfaXmF0CanjhqrnCSBnwq66mtHFu6mFxRdc8WeHrLjztrjUe/f5vGBuWJmosbpRqIkusm9cw43ki8l9xQAsz88HXq1TIT5+kQsKUiM6rwEwniUkgZFc553e8y6K2UtofAIIv1uj1kXzfE3bNhg3rNnz4jd1759+3RJSUmB8+fPy86ePVtfX19fd+bMGcWBAwdUANDa2ip74IEHBuvr6+t6e3vZP/3pT/Hnzp2r279///nq6upJbbteeOGFpLi4OL6pqanumWee6a6rq1NeOi73zDPPpH/66adNdXV1tZ9//rnyzTffjDtx4oTCZDJxzc3NtU1NTXX/+I//SHzgZ4BJE3SKomQURZ2iKKqaoqhaiqJ+dtXr2yiKEimKGvPJRlFUBkVRn1AUVX9p33+eyuAJsxeaosEH/DB3d17DUWaPc8swfo8HqTnGcb3Lw8FpHkR3UwO6G+tg6+uBTKVCas4CpOcXgaKnWHVGUeCkUjAcN8r2sLuxHgmGzCmr1qs+3o8VTPSLMotVcuTIpWAvveVClA9IHlGE/9K+IoCUCCrxTho4nilF0U0GaBWRVfAJhPEgDYrmPr3eQFg3hF5feOOuZtmyZe7BwUG2tbWVO3HihFyr1fJnz56VHzlyRFNYWFh4qVIua2hokAGAXq/33XLLLUMA8Mknn6jWrl1rVavVQnx8vPAP//APk7oSHD9+XPXtb3/bDADXXXedx2g0ugDgs88+U37lK19xpKWlBTiOw7333ms+fPiwKj8/39vR0SH97ne/m/Hee+9pdDodWRQ7A4STDXgB3CyKopOiKA7AZxRFHRBF8W8URWUAWANgPMuJAIBHRVE8TVGUGkAVRVGHRFGsm5rwCbOWKcmtw0nSJh4TbR18vP0Gu4K/6sMV6KnA43Six9kMAIhL0UMZp4MmKQU0Q8NpMcPWG72sUaZSweMYrTEPOuOwsPX3jjjVTAUZlj5AE11jpNOOoE4/iWORKZeAF0R8RRssBP3NNhTRsRQ0jeu1SlxwedHm9iKRYzDgD//zpEouIunGZBQ2DaGuPTwHHgIhFAxNoTiNVNDnOilSNiz/1xRJeONCcccdd1jeeustXU9PD1dRUWFubW2VbN261fTYY48NXDmusbFRolAoRq3LH29tFMuy4rCE0eVyjQwSxymAjLc9KSmJr6mpqfvTn/6k2blzZ/I777wT/8c//rE1gssjRMGkFXQxiPPSt9yl/4bfxf8E8DjGyWdEUTSJonj60tcOAPUAxiyyIHzxuJYGOxExXatEY2T4QdEMhqwWmJob0NVQB1tvDyRyORIMGcguXYLUnAUTdia9Go/DAYYbvUBNFATw/mATo6mU8lBT8J73+wOosrtwxunGSdsQenyRf96dd3tx0jYEGU2hxxfAfEXkHRz7GeDzfAWWFhOpJSF6itI0kEvIAr65zj2p8RYZTU14g5PRlHBParwl2nPcf//95j179sTv379ft2HDBsutt95qf/PNNxNtNhsNABcvXuS6urrGFFVvvvlm5wcffBDndDopi8VCHzp0aGTKJiMjw3vq1CklAOzevXtEfnPjjTc63377bR0AVFVVyZqamuQAcNNNNw2dPHlSbTKZ2EAggD/+8Y/xq1atcppMJpbneWzatMn63HPPdZ07d04R7XUSwies+XSKohgAVQByAfxKFMWTFEWtA9AlimJ1OM4WFEVlA1gM4GTU0RLmDEJghmbApi2RnvjAFlMXFNo4uGxTU2FVJyYBogB7/1hnLJ/bjcHODgAY+VeTnApR4AEx9GdGfFoGBrs6IAoihqzmKYlxMmhhat9zEQAb5QMYCyBJykHDMRBEEYVKGeoi9FgXKQqfpbFYIdPj75WmqOIgfLkpy4pKkkyYZeg4ln/QkGQK5eIyzIOGJFMcx0ZdpVi6dKlnaGiITklJ8WVlZfmzsrL8tbW1suuuuy4fABQKhbB79+6LLMuO+nBavny568477zQXFxcXpaene8vLy4cLqvjJT37Se++9985/++23E1asWDHi0vDYY4/133PPPdlGo7GwuLjYlZeX59bpdHxWVpZ/+/btXStXrjSKokjdcssttg0bNlhPnDghf/DBB7MFQaAA4Nlnn70W7SohTKjxpjRCDqaoOAB/AvDPAF4D8A+iKNooimoFsFQUxYFx9lMBOAzgeVEU944z5ocAfggAmZmZZW1tkXVrJMwuTh/4Cz554zfXdIzkeTnou9gy4RhtcipsfeNLQNLyCtHdGLmiKmX+AvReaJ5wjDohEY7BkL/yEaNNSZ1UyiJVquAdck44ZhhDQfG43vHTRc/67+PNhOwpPeYitRxnHe6IfNav0yjAUBT+f/bePEyus77z/bxnq71631u9SLJ225JlG29gTMAZs9gXhgQHZ0gIBCY82RguM/dJ8CQz+IFJJpPMEJYkDDdzh5AAAw5bWD2QsQ22MZZlWbJ2qdVqdbd6r73qbO/94/TeVV1LV0syPp/nabW66ixvVZ2q+r2/9/v7/p5OZLgpFuZQKosKbGT6cHsSXnj6El29MVLJAsmEJw3af0cP05dSXLzwMnIo8rlifPKdB3jzDbXJvnyuDMePH2f37t0AHD16NLtv376SXsDFfNCDinCvJR/0SrBtG9M0RTgclseOHQvce++9O86ePXs0GAz6zSKuAi+88ELrjTfeOLD69qoq0qSUc0KIfwYeAAaBhex5L3BICHGrlHLFRTqvW/8q8IVSwfn8sf8G+BuAm2++2b9IXua4G7Tu86gke7r+pVK7AKb8JShKdMqsBlU3EAIUpfwyeCGTRjUMnAp042NnTtLaN0AwEiU1NUmiSGa+3iibIGs6nMpxW0OkYh36vkiQZ5Oenr0vaPD8vLZ9o1fjU3G4/u5ezoUF+/OC5344jKIKcgmTQt4hFNLI5erbubRFV1EARQgUrwkuivD83RXhtQJT8O5Tlt23/HYhQBUCIfG6vLped1hXShwktgRHer9NKbGlxHQl01Vo9n1K42fQf754eFv3+O/0tU98eXym6bJp6x2G10l0I5nzq0EqlVJe/epX77QsS0gp+Yu/+IsLfnB+7VE2QBdCtAHWfHAeAl4P/ImUsn3ZNkMUyaALL3r/HHBcSvnndR25zzVNPQJ0WYlkoowEYjM/cZa7otSK6zhI16nYgjLS0FRUBrMax7KYGh4CvGz6lQjQRQm5zUbJuS6aALuCFzOiLU10egI6w/n6FcHazQGymTzJaIAt/XGsG5tJAKmBEIYQdJ1Kce5UfeRETZrK163Kaw3KoXeGscYra5gl4wavtuqzMvRKprshSFdD/bsC+1xdGnXNfd+W9pe1zWBTU5N79OjRKroG+lwNKokwuoAfCSGOAM8CP5BSfqvUxkKIbiHEt+f/vBP4V8DrhBCH53/euOFR+1zz1KNItB4Z6lqpRvp1JQlGo1Xv49g1GwtURaKhZVOO+0Iqx3UVFno686/bQMgrjA3WsYj4eCZPVFUYcWwar29lqGAxVLCYtR0uWzaBwDVcDFjF8yCcl1Uy8JrlJj977uPjswHKZtCllEfwijvX22Zg2f9HgTfO//9JrkUza59Nx7FLL/frwSCRhiZcx8F1HaQ7HwzPXykLsYRmGMRa2xBCIRiNogeCmPmc15peSkDg2jaxltbFTHkgHMHK50lOXiYUb0DTdRo7utYEKKLIH1Iu2VUZ4QhNXb1rB79kVOV1SNU1pCuZHR9ddEQRQkFuUjZZD1Tf7dLMbV4be6e1g/E3vI3Wky/wrWBzXV1hljOUK5Qt9OwL6ozMZ8yHciZdhk6+zuPZEw3xTCLDs0VEM5tlKFQPqppwOtfm5PTlxs1+gO7j47MB6twVxcfHwwgtZTzjbe3oRhAtEMDK55gdH2XucnlXjPTMklygElkHQHp6Cj0YorGzm7nxUWzLrOhcANGmFtKz3sqlHgwyO1ZdobpmBDBCIRraOxg7fbKqfSslPTODomm460yAVlMvp5livPj23+QHBOHWnk0LzgFyruRcNs/+WIjDqeITjuG8xfZQgD0RjUnT5ky2Pk2YlnM6m6dBU0kUcSmS13KEXg2VaIl8ynKwv7n8Rj4+Pj4l8AN0n02hkM16mW3p6aGTkxNX7NxWPsfc+EazxoK2/kEmL5yveA/bLGCbBaxCoa4OL8tJTIzTsXU7l8+dqXifXCqJqhs4Vv302ABz9/2SF5xfIfLSKxq9vSHCM4lMUWeXgusSVDUmLZsboiGadBVLSqKqiq4IkrYzX0TpMZw3ybmVB6QzllOyaNUI1u/jVFfqHOxXE3P7EpcNE9JVdnXFrvYwfDaBWctWvzw+03S5YOsdAa9ItEnX/Kpqn7rjB+g+m8ZmBKibiVwWxaSmJmho76Rz23VI6cltLp04VtFxrHyOcEMD7QNbmRg6V/dxXj53hq7rdjF2+kTF+0Sbmte1o6yW7F1v4H8M7N/UrHkpnkpk2BsJIgREVZWc4xJSFbKOy5F0josFT3N/JF1+ktasq9wQC/KzRKZipxenyGMOKIJ82mTbdU2omoqqCzRdpceCmxIuQs6ro+ZdVhbCb4EnjRHSu8UVEg2BBhjo2BNZ3OzG3WHcnI0xGF8TqDtJE2dmlWxIQkgRVU1c1uOupgg3R0Joive4Mq7kL0emiKsKH+5tW3ShUfHcZ1SYd6MRCOSK52rlv/Dx8SmGc1emxqIabtzSgK5evRoan82hmM3ix8+NbbmWbBY///nPN+7Zsyd/8ODBknrAL3zhCw3Hjh0LfexjH1sz5nA4fCCbzT6/uaP0qQQ/QPfZFJqinVy35zYAZhPjTF0auroDqpJcKkkuteRt3bKlv6r9rUKhrK/5RihkK7MdXCAYjZKo0yKGq2r844HXYV1FK75j81r0LkPjsmlX5ZO+nBnL4ZlEhp6ATmdA50KuwFSZx/VSOochBOayQL3gSl7oNYCVXVvvzOm88Ujlzi5Kg4E777Fuqnm05mB9AvSkiZlcu4JiDMTXBuhAVFXI1anx1IONcfafX3a9xnT+EvhkXwdbz1d3Ha9mR0vwmgzQD/T5+vOfNz56drSzWKOivCuVhduvhSD9a1/7WqNt24n1AvSHHnooASSu4LB8asCf4vtsCj36ddyUu5ubcncz0HHD1R7OFSc7N0u4obH8hjUyc+ki3Tv3VLy9ZlRfXFqKws13MWlfGzKIgVCg5uB8OZcKFs8lswRVheujIXaEA/QGdLaGjDXbZlyJJqBVL5/f2EgOWu+KYE9uXoHvekT0+jnS5FavOMy/YF2FjWfoI9dolnpHR/VuSz7XLrOWrX5uZLJrvW0+NzLZNWfZNV2QH/nIRzoeeeSRdoD3vOc9W2677bYdAF//+tdjDzzwwOCjjz4a379//649e/bsvu+++7YmEgkF4AMf+EDPtm3b9u7YsWPP+973vt4f/OAHkccee6zxIx/5SO+uXbv2HDt2LPDII4+0L2zz5je/eSvAJz7xiZZ3vetdfQAnTpww9u/fv2vfvn27f+/3fm9FV62HH364Y9++fbt37Nix54Mf/KDfcesK42fQfTYFsUxDKzbVjbzMOKop3FtHrpGdm6Vn5x4QMHnhfEXOKK1b+nG7S3aG9k4J8wv5xdENA6tkYyLJln03MvLSi3WxtawUNZ0sKvO4Glh1HsdI3mKEpYxsT0Avul17QGcot76mf6+j8uDp0q4zRVl4OLrAGqmsa+xmYNRY8PrpwU5iUqxwtOnIrw7Qvb+/jEn/QAiQvHbcgnz1GfuGazRA397m689/nvjy+EzTcllLMfKuVL48PtNUi0f6Pffck/6zP/uzDmDi8OHDYdM0lUKhIB5//PHovn37ch/72Me6Hn/88VPxeNz9wz/8w86PfvSjHR/+8Icnvv3tbzedO3fuqKIoTE1Nqa2trc7rX//6uTe/+c2Jd7/73bPzx+68cOHCi6FQSE5NTa2ZeX/gAx/oe+973zv527/929Mf//jH2xZuf/TRR+NnzpwJHjly5LiUkte//vXbv/Od70Tvu+++q/fB9ArDD9Bfxri2p21dErUuCVyrCkyLIG0XN2fj5m1wJNKVXtCtipW/leV/K0gBwmt1uHisJreD/ft/kcOHv7ehMVVLz+59XKqq3X3p5yyXSnLp5EuA1/hnpMxxA+EIF4+9uGG7xd7de7l0fH3te+e2HYyfPbXuNpU2QiqHRHDsNW+iTvLkDVPvAH01XQGdZl3jsmkxYS5JTZo0lTlNZa6Im8sCGhJ9rLLmQAsIbT4GuFLPb4lLvtjT2h3Q2B8P40o4k81zJrt2gnL9tI0oIqVZwbyN42dHl6Q/TzS2IWoI0OPXaIC+ta1+TaZ8rj6XC3bxmfrq7czKtlvNXXfdlf21X/u1yOzsrBIIBOQNN9yQfuKJJ8JPPfVU7I1vfOPc2bNng7feeusuAMuyxMGDB9PNzc1OIBBwH3zwwf43velNiXe84x1FJSs7d+7MvfWtbx28//775x566KE1ll6HDh2Kfuc73zkL8P73v3/6ox/9aC/Ad7/73fjjjz8e37Nnzx6AbDarnDhxIugH6FcOP0B/mZI/PUv6yUvkT86W3mixAo2loH3hNrzfi80whUDvjWKNppEFB2nWFlgag3HM88kVtzUlWohpcQ7zPfRgEOlKbLP+FnirqT5zX9n2I8eP0to3QHpminy6+GdVa99AxUWl61N+ojV+9hTtA9uYGDpbcptsYo62vkEmhyt3pSnGuc2DDCgAACAASURBVF//II/J+sllNsoLqRyDIYPzZbLZtfKzpBdgN2kqO8JLj/tYOr9Cg16MSpXRek8UYXhvRGdu/n1xhQL0Uvr2Yqd/qL2JBy564zs82MJvn6/MvnTtSdd+tkil+oYZIqJV7QjZqttMWZv7tdfdECQS8L9af57oCGgVvZ07jMq2W00gEJC9vb2FT33qU6233npr+sYbb8w99thjsQsXLgS2bt1auOuuu5Lf/OY313x4Hz58+Pg3vvGN+Be/+MWmz3zmM+1PP/30mkzNj370o9Pf+c53Yl/72tca//RP/7T79OnTa7JLiqKseSdJKfn93//9sQ9/+MMvL7eHnyP8T5GXGdKRJB+7QOqfL2L0ltE5SlakwmSRr93ltzizBdzU5hRcabbO27f+36hSZbZxhu8//9lNOc9yXFcSbmis2Ae8mmYuU8NDRJtbaeyMId35Z1a6BCNREKKOjYoqG5MeKt1SvHf3XhRNY/rixQ2NZOJtv86jwWvP27nd0DctQF9g1naYXSdbXoxKRyQMZc2kdiMRutYZQZqOd4z5wyhhDTdjs/gpsNAbLKSixOZ19nLhPsn/yAN6yFsJUwVSVxBzS9f0/okCj7e0A/AZ3fvMeL+jI2YqmHjbkn9u6+DRgMMnRrzvflcRFRdEGYNxnISJLDj8ahLe2bS4Ks8/xxX+/YXiPRN+sTHBATGKfeoQiq57n41Ses/I4melnP/IlIvPx9yu1/G5mbVStT8wnkLOTiA0DVQNoemgaGzp3VvhI/F5ufDLnc2zHz83tmU9mUtQEe4vdzavkzFbnzvuuCP9qU99quMzn/nM0MGDB3N/8Ad/0Ltv377sa1/72syHPvShvqNHjwb27dtXSKVSyvnz5/X+/n4rnU4r73jHOxKvfe1r0zt27LgeIBqNOslkUgFwHIezZ88ab3nLW1L33ntvuru7uzmRSKyQudx0003pz372s80f+MAHZj772c8utoO+7777kn/8x3/c/b73vW+moaHBPX/+vG4Yhuzp6dl41bpPRfgB+ssIO1Fg5h9OYA55X+ZOpn7vE7UxgD1R3XJ8NShRHeaTzeFchDsO/hLPnfgOhczmrZaNnnyJ3t37Nq1RT3pmbWIhOTmBEQ7T1je4KecsxeTQ2ZJe57ZpkZ+dJd7WTi6VwHWqCzSDAY09d+3iobZt9RpuXTmSyqJCxTaJVwp7I2nwDezqJAvIIpnxxez8MrSmIG6qxFRimR/6mux2xkaZ//zZ0hcg4Tho45Xr7bXJHO0DQbaGDT7U0cwhCe3RyOKJBi5kKFn9K1nhPLM8YmpoDJc85w4xjXPqOQrpVMXjBNBliVWGxBTpidEVtymqyt6HHqrq+D7XPk265rynt22smIvLAu/pbRtr1LWaMzN333136hOf+ETn6173ukw8HncDgYC88847093d3fZf//VfDz344INbTdMUAH/0R390qaGhwX3zm9+8vVAoCIBHHnnkIsBDDz0081u/9VsDf/VXf9XxxS9+8exv/MZvDKRSKVVKKd7//vdfbm1tXfFR+elPf3r4wQcf3PrpT3+64/7771+cYLztbW9LHjt2LHjLLbfsAgiHw+4XvvCF836AfuXwA/SXCbmXppn9yqkVS9JOosoCtHVQmwJFv8DrgRLR0NpCOAEVJaghZjS2zG5lZvAAJ44+sSnnXMAqVP4cbVS3v4CZzV7xtu9mLkfXjl2MnSrijS5gbnyUufFROrfvYPzM+nr11dx5Q5z9o5/hyegEf9Z+P8dEI2+xhvizwP46jX5j5FzJwXiY55KbN8GsBXMjUbbrZdZrlZqtYRMlM28VBs50Lc+9YGsowI1DWf5VKM/5rElUVfirvo7SwXmV6MKlWXdRBWiuhXRdIo3N5DPpiht3BV2T3oCNJcFyBTlHkJMKSIlmLLn8BJvbMHSd3t376jN4n2uKBQvF1T7oQUW49fBBf+CBB1K2bR9a+HtoaGhRinL//fen7r///uOr93nxxRfX3Hbvvfdmzp49u6ivfO6559a0tf7d3/3daWAaYNeuXebhw4cXvziWe6M//PDDEw8//PCV6zLoswI/QL/GkbZL4rtDpJ9cWeSnxA3ccsVYlaKCPVWvYH9tZKq1RzDPe/UrDp52VO+O0JvegbUrz9kTz9bp3Ctp6e1jamS44u0b2jvJzNW8QrkCp0o5RCk03VjxhZ9LJZku8ZiWZ8Zb+/pJTXtmAhPnlzVLqiBQUxW4cWcTtgNHTs0yGJmBNGw99VU+feqryHnfmXv2vZf/3vgatjhJ7sm8xGPRvXxKvzrBSe4a7H6ZVgVGf3yZdIR5WcX8Bq5ESlnUSlFtNHCSlcvN9K4IUoISUjFHi61KlXjh6zCRVByJU0OB52uHcrx2fgCPtLcC0D+RhyLe6MZA3Fs5FCyuIBZj9aO8tzHJ1kP/AIA9/1PIZioqrF7AOfwYb132d3T3LXw8fzMfD98PyxL2v9Q8xa/sa0Qo12bhqs/GeXhb9/jv9LVPfHl8pumyaesdhtdJdCOZcx+fUvgB+jWMPZ1j+h9OFLVbU6N6XQJ0YzCOLDhYoxtrGLKAPZlF6wijhL1Ly83Z2FMrAxCZsbEyNi20EtdezWTLBZLT9Z+kh2LxksFsMfLpVNUdOkuRqYOspmf3XtKzM0xdvLDi9ubuLWiGvljs62nnBa7j0tY/SCGbITM3R7SpiemRlbrzyQvnMEJhzFzxjGc0ovOug3OEJp9AGgZ33n0DoYlDK7ZZKL49ePS/c5D/vnj7rdEunrrl8zzv6lfcWPNcNn/NyVwKAswLpYPJ9XAyFtVY5YiAilVF4LqAm7YWNd2u6SDTNdSg1GG5qH+ojNRt4RRVXlglN9/AkOXkMP+uc6VZh6uoGGND3Phv/rL2A/u8LGjUNbcWK0Ufn2rxA/RrlOyRSWa/ehpZKB5yCKM+jURk3sEaq09wDt4Xvpu2wFC8b0dr/cSCbuvc0ftWntG+xezl+lgBLmDmq2vyMjN2ic7tO+py7nq41ExdGCraMXRmtLJiz3hr25rbHNumY9sORuctI5dj6PDQnRqhQh4a+xCRdsKqBr23wsWny55PTY/xmT//EH/4e/+Zx8TmOL30agr7cym+pa+0sctLNtXNpVoMIQgqG4gCLYkIachcZXJPJ2WiNpaWqbkpy8vmC3ASBZxZbzt7MgfTOXBBbTCgKbB43zVFhYH5Qp33tpBFf9CkX6x1nlNUFbtkb4HyZKYuw9TaQtT2fTeiav5X6ssRKWXdJI4+PtXguq6ghKjP/zS5xpCWw9y3zpF55gp1DN6sz6QqtLMNyUZe2/hL/OPEf1vhOtPRtx1N1bl0fo3MriJSU5MVb9s2sBUhBHNjo+U3roDmrm6yNcplWnr70IxAxYF4KS6fO0NzzxZmLq08jlVk4tIQM3jopgShi8tqAubmVx+6b6r4nIqh8dbvf4vHfvFf1jTm/arkXT/8NseuP8Dft/aQW5ZF7tAUPv3vP0h4coJ9v/dvWXAkEVIysvU6fuBcGx9nQUXwd8dsBoY3polXIzp2pQH6dB59SxQnUSgezDpyMZtvDMZXBuELb1VN2bQ6lI0inepS57/sHiJ96NCa241QiHBDE1PDQ3Ua2RLVdPb1uXYIBoNMT0/T0tJSfmMfnzriuq6YnJxsAIo2Vrk2vtF8ALAmssz8/XGs8fJf7KX8i1+uGGaAB3b9Ll7nJQ/F1jAsneQt93Aq9SznTj5XsX2hoqrkUpXLC6TjMLlKSlI7gskLQzXvbeZyBKMxrPzG6wL0YHDNbZPDQ/P2k7PsHGzkzv40jVNPICZKZBUzlU90wv0xdn/tK+x409s5Va1JNfCvv/YP7Pz2Nznwxb/jVzSNmR27mB7cxlTvFg5++e8JzXrNbX7xv3xsxX7/82N/wWW1tIPHZqIA9xlBbGB7Hn79e5P1mfdWKWW2LqbR2kIoEX1dnXYxRFD1XFuqDIS9navfpVoqnTjcPGvzvzs7+MYzLxS9v6mrh4mhc0Xv2yg9u/wA/eVIb28vIyMjTE5OMj4+rjmO03q1x+TzisEFjtq2/d5id/oB+jVC5rnLzH3tDLKMJASWFUzVgcXOhdcAwfzKYFJtCqA2BokPC252XseevbdxVnmRUyd+UnaJOtLYRGq68v4KUxcv0NjZjapqTF+qXLdejHBjY83Zc4DU9CTZVIKe3XsZP3O6YreJYlw+e5rO7TsRgCtdcokEyakJWnu6ee2BHG2XvwXFbaOXqCZA75YI4JePHeKRnQeqHm/7ySX9v2rbtL10lLaXyneDfcvf/CXf/IOPM3UVikUVAeeEy//8xjSWJlbGqwq1O5LUsuQuAU3BGIyvuV06EqGAXD1xUjy7xVqlbldCGOCmTM/LvUxiQiRMAgl44LYP8rWn/nzNhP7yuTP07N7H5bOn69osTQiF7ut21u14PlcOXdcZHPRscffs2fOilPLmqzwkHx+g6hyNT71xCw4zXzrJ7P86VVlwPthQfXYsrC01I1mFOZxa+2V+jSBtiZuzUAIqQlcIZ8Jcn3oVbxn8AAcOvJFgNFZy33hbR9XnS05OkK+DL7tSBxcHxzS5dPwY7QMb91NXdY2xMye5fPY0yakJ9ECQQipB2+XHKjuAnYdA6ed6ObrmeUzf+bd/TeMVbMMeTMxxT2qm/IY18p8TOl8a13jymMsXJjR+eBo6XS80tSWctyzec38rP7qlaeWOG9Gh17CrElIxz8xhnk+u/BlKYl1MYV5IYV1c6QNu9MWxpnMYA3G01rUrLtcEAQWqSCYEsgEMo3jzrkvHj9LWP1hXt5Xmnl6M0NVZwfHx8fn5xA/QryLmaJqJv3ye7POVOZgYg3Gk46JviUGggiLRgIIxEAdb4mY9twYRWrufeT6J3htF3xJDbbx22ri7KRN7PIubtdF7lrqmGmaAHXPX86aO93PbwX9JQ+vaYFy6LnqwdHfNYqiaSmZu40FetY2A1qUOdiiOaa5YfrcKeSYujZHVq1jJVSpbbFMsL9seTCR463T1reBzjU3lN1qFBN7/p5/hf4Ubq963Ug5M2Wx7cZbgpQw7n58lfi7Fdnfp43NA0/nU92e4+9Aq954NBOjVFK0Z/TGUBgPzYuUTTBHT0brCmCMptKYg5lASJaKX33EVVTTgrRmjM1Kxa1W6O8s/nvhvFAqlVwTGTp+gsb36SXwp2gevzSZePj4+L1/8AP0qIKUk/fQoE58+vMaCsBRGfxzzfBJreD4DZjpoHWGMgTjGYBx9SwytI4yI6qB4MhihKJhDSa/ttyO9duKud99qrJG0d1xDvTYz6kViFc1V6Z/Zzr2xd3H3wV+lvXfr4n2jp47TPrh17U7r4DoOgUi0/IZliDbXr9iomItLtYyfPc2lEy/Rdd2uxdv6tvYStiqXAFWazlVSFzG6vOvnjX/3uYo/YLZqCm908kzVEOi4msZMFZaE1fL4SWi85HW2FCENtTmI2hjgV7IqNwbmJ7QCQnmXYGHlKphQr0wGXZoubqJ0AKs0GBiD8cUffUsMmbVRdBWjN4Z9ufaC1itiflHhREc0aXz/mb+hkC8/Ucmlqusouh5bb7qlbsfy8fHxAV+DfsVxczazXz1F7mjlNqpGX2ytn7Jk3S/VUjIYWXAwh5KoLUHUqIE5nERt9pa1nek8zkQWmq/BZe514i8Fhc6ZHjq0tzN7YIaT6Z8yfPoIbpXNghzbJtIUobBBmYtRJHOvBYIYsTjZqer83tOzM/Ts3MOlIraIlRJpaKCltYFUYpo7btvOhct57g98vW7dGlfTeFMHE/+UpPXYi/yCNPmBKC6vWuA+O8vv/D8fIh6PYl0cqfp8jm7QrAgydQzShZTc7WgMOgrh6RTkvGtJZm2ceR30q8cCvOqpJP/1vjYoZR++kei1jpGvEjW8CfoqzOHVQWoN51QFSkTHzdTgoV5HRIPGY8N/h2WX15bHWlqrqlFZD0VVGdx/sC7H8vHx8VnAD9CvIObFFNN/f7xyn2FFYPTH6lYQuhxnOo8znUdtCOBMe24hWkcYJah5Xskz9eoseuUQQtA818Lt3Me+G+7idOscoZYO3KOHKKTLZ8u6rtvJ2Ok1XZEJveo1KOdPUZibwXVdItftBkVlcst22o4f8gIpI0DqlBdEZ5MJwi2tSCmRO65HtUy+uu8OTgaiDFo53jB+lrZLQ1zuHWQy0sDWyUt8v38vzVaBm8bPETt9lNTIMEiJmcsyduYkLVv6ma7QZaarr4dMOkdyZoZgJMIbdmbZmvwWogXkHNwUiWM41U5CKg/cIj1L/3/bD77JD+5d33LRFQqhxFzVRXsiEiGwbRvi3Dn+5FN/wjvf/+Gq9l9NtxT8RlbjjmmH9uEslJmoLUyQ3/X0HOHM/GQwoKI1GoiAhhJQKZytvWGVMBS0thCoAqEquHkb5NJ7U20JooQ0nNkC1sTaybreHfEcoVyJfanC17uG+Nw8n8QYiOMY8zaNm7GYUcExc5EcU1OVvUdCsVjdAvTePdcTCEfKb+jj4+NTBX6AfgWQriT95CUS3x2quDug1hoESdGsVz1xEktBkX05izEYx01tXrMXYyDudRetYkld6wwXbYe+HrFUjMyefv5j4x7e0reLm5/8J5x8jtyMt3IhFIXQgdsY6RlEcx2GYi18u6WL23afIJ5Ncba5CwRcDEZ5PtTIzj238y8uneIrW/ZwSV+WIR/Yv/jfP4p/G3nqGHPX7eNPdt6OLiWW4mn+I6qC6bicDMQ42b8f+pf2o2XA+x2C/x3vgB2384dHfojz7BMk3/BWPr3lel6fGuc1T3yLVAVB+szkLL+5/aekBru5qLaTD7Yh5ucnQkDA2dxrylCWPPx3/uNX2PXGt3NiHcvFY4GwF3/lcqhtbTiTZVxjhAApCQwOkj9yhOAN19MzPsa7Z8f426aumsf9nqzOA09WvrLl5my0nijtEpSYwJ7J46Yt7MtL16raaODM1fZ+Wv3e1wfjiPkAXYkbqGEN82IarTeKO7Iqey3wgtpqVxVqDK7NoSQIvEx6Ld1IN4CIaBQaTI6NPrnudj279pLPpMCFmdH69DsA2HbwVXU7lo+Pj88CQl6JCp8qufnmm+XPfvazqz2MuuBkLOa+eZbc4Qqt6hQw+hswhxKbk4kqg9EXA11Z6gAqvH/MsXRVzYdKofdEsUbT6L3ruIKsyuJZF1PVPxcxndfeFiQ9L4JudQr8wuwYOUWjLZ/isdZ+LhgrXRf6ggbD+donJzsKKW5283wl0IS5rKgyKOBAPMJTier05O12gbSikp0/1oCZ4Z1//xdl/dHvvzXMYOpHaMw/lsZ+SE+CvYHGOeFWyFaWcZQIzj2+C3PU6+J45O0P8nu/8ADgvbRbNIXtVp7B2Sn6Lw7Re/wYA//nhwggsGcPhZdKy3mMbduQhQJC17EuXUIus9vMNTUzeuBm3vtL7+aPXnyG5onLfPIXH+D0qsnBzY5KAslpdeX1/J6Czm/9c3VFwkrMQAko2FPFXxMR1ZF1ClhFSEPviuBmrBUTXL0v5tloZm2UiIabdxCGglVFwegCRn98rZyuDGpzALUhgHk+idYaxC24dZnkq+1hsB3UWABpu1hFVgGSXSm++9RfVdQfoWfXXi6dOLbhca3mvX/5ORrqWHDqc/UQQjzn2yz6XCv4GfRNpHAuwcwXT+BkTJSYUfZLS20Ogiowz69tT32lWKtJBbE8YN8oUoJkjdVbvfnRvhhpZSkwmlIDfKl1YN19ugL6hgJ0vaWNv0+vDdTyEs7mqvdcntBWOuoMGRG+9Y7f4f6v/hWFdAo9GKRwx+uJ/OwJYvEI0YhOwXTZlvoiynKB+dwF6D4Ao89XPYZaEEhaX9PF6Be96/iGr3yRt99+N18JN/LffvCPXP/ol0vua4+PozQ34854gXLowAGcTAY1Hse+fBnr4sUVQflyQrMztB8/yv/3+U/T95MnkP/inXz2JUk4uTJAVrJZpKHyb24O84S2VKfwecPkXzcaiCoy3mpTAKvIe2YBvSmIG9FRwpoX+G7gbSRUz2N9xeqTKrBncwhnvnnZRlUbNVk76ovZfiVmYM/Ub4XGmSngzJR+7xScbMXNyzaDtr4BPzj38fHZFPwAfROQriT1o4skH7uwmPlVDAUZ0pDFWneL+eZDG/wC3yzUlhD2+MbdRMCTBWw2ssHg4ZhJtdGGtYEiw7imMpYvnSmNKgrVlYcW50iogdffdg+NJ18gcddt/M7IJ1G2XMBw52UVpep7R5+HvtshNwt6GEbXtkFfnwqeS6FBQy84BeLOUUY1A2zvgv7Nj3yIi//1b3jiznvWDdCdmRmUSITQ/v3kDh8GTcM8fbpiL7/Y2CixMU++0BBoRJ4vHjyLnMPHThu8aSck5x1CTCEY7w7TVUWAvq4VYkABTYDpOSgZfbGiE+Cy6MLLIhfWFj0rUR3puBvqLKy1hnCy3rVrjlaWdTcG495nlfC6fKpNAdy05dXX1OszrILXfDJZefdf2yygajpd1+1kenSEXKL2+oAFtt96+4aP4ePj41MMP0CvM07KZOZLJymcWfnhb0/ni3YA1TojYDmbrjXfCEoR73TwsmVqgwEIhJBIIRY7FuK4YLsIQ/XaiAMoAvPs5q8OfG9vlLyoXlZwNJ2jUVOYs6uPMPZEgjy9joRlOG8SURUydeh0+cmtN+FsPUirMPmglUVzK9TnDz/l/e69tfqTrg5EtRB07gNVByvvdRtNXoK5IYj3Iqwkbb+4m8l/Og2Akcvyxx/6LWID/SUNTxZwMxlyx44Rvv12ci++iN63BetC9d1d1ba92OtklEPDaf6PFWYupPLtHp2LGgStKgPdEvG53hvFGst4gXl/zLM9NSroXVDsWF1RrOEUIqyBoWD0xxABFdd0wXSwRjc4eVYFssoAX5pLkhOtM4I9nkGENM/StR5oAjWi45SpPdkrbudFflTRIS+fOwPAyPGjNHb11CVA33HbXRs+ho+Pj08x/AC9juRPzzLzpZPFi6QUVma5FhxaruHAfAE3a6PEdJYqz7xfWktwfYcZBfSOyOJjVBs2vwmSbArwH6PVZ88BTCnZHggwZ9ffwWZbOMD5XH2Kbxf07VvdFGquhsZKU6eg7w4Y/kl1+2kh6LreC8gnT8LIs8W3S45A7600RS4zqSmLWfRgOoV1+jSBHTsonDpV8jT6wADOzAy5F17wTtvcgptK48xU/lijr38Ie6p80x01oBE7l+Qd5yo+NOA1BkIIr16jCAu9BwDMC17WXGurrnEWAEF1UdKiNQSQrsSazCKzdWyG5Uov+JfSm1wv1JqowvsxXe/tJCieHZ+3MxW6UlE35HKIkIreESmqOV9Nqqm2z09Ri5ZnFS29fbRu6d/wcXx8fHyK4TcqqgPSkSS+N8TU/3u0pIOB2hLCmdegq40B1JbgyyI4V6I69uUsMu/gpkzclOX9pK0K7B9FUfu3zeRbe6KYG/CPVmvct9xifLOuYdaxIPtALMy+gCTTvKP6nfNzkK9yJaN9L0gXLv4Uxo+AU0ZTP/JT1JZuen91z8rbCwXMixfRe3tL7moNDaF3dyOzWWQ2S+7551EbKmueFbzxII3v/s8ozfdUtL01mvakKCUwBuMocR0MBa0zjN4TRW0PY15Iedf/stWWwPZGtPaw5zpUxKbUnsqh961THF3s/B3hRWmLNZZBWm59g3PAnswhszYy56CGlnI2Rk8UTBdjII7e63UZNvpjaN1RhLH0nAlDRe+JeuOs8RrXuiIoYQ0loiFNF/NCsqJg/9zk4ZrOF6mhY+1q/Oy5j4/PZuIH6BvEnisw+dkjpH50cd0ozZnKoTYHPb/gjFl26fZaQWupIeu3gCsXs4geclOvOLclyCOR6osxl2PU2Jq9nH69XqG5ArTqGs+nsjxr6kTHq9WSz6NX2YwqPVo+KF9O901w9ofE8t9ny6/v9Pz159Ha27Gn1nc1UqIrO7qa54cIHSzdDCZ04ABaezvG1jtwZhuQFToOSdNF7/A8rJWwNi9F8S5SrSOMeT6Jm7TAdLHHs1iX0l4zr2KoAnsiiz2ehWK2kpLqL4Rl16PRH19f814XhNedeCCOkyig90RBSoQivASDBJmzAAGawOiL4eZsrEvp+QC9xtNaDm7Wxs3Y3mdGhcepdj7Q1N1DqKERhKRj63Y6t+1AKAo9u/aU33kVO2/3A3QfH5/Nw5e4bIDcS9PMfuVUZQVaksqbhVxLSInWE61LkaiTMIvq8OvFP+6O4IiNyUj0GgOgQ6ks10dDvJguPvG6kDOJayrJKrubruZgPMwLKe8cB5wKrTuLoVUZoAcaq9u+sFQMGc3/iB0PNuG23ICSOI1VuMzc5E6mf3AMnLXPR2DXLsxzazUnhZMnIRiEVTaTxvZt5I8dQ5omSrwLp8rFAWeugNYVwU2ZmENJtG5PU40iUMLauu9vN1XlNV2qBkH3rjsR0NAaA0gXlIDiOSjBinMYg/F1V99EyJOrCFVBaAJUBaHOX9cL17eUoAic2cIK3biTLOBaDlpjwDuOYHGyY/TGEIpAbQjgmjZK3MCeK6CEdfQeDTtlQX7V66kpKMuy7SsC6uV/1BjYhwLR8hstI9zQyNzYGJdSLyFd73G1D27DsaqrWWnd0k9Lb19V+/j4+PhUgx+g14C0XRLfHSL95KWrPZRNx8lYi51G60E9NKrFcNpC/KdwgZp84upEukiwucCYadEb0MsWk5ZDEWJRKvPLiWdqPg7geZsrGrRsY6m2oESklKziWo91w/TpFTeJ/CyqyIOZwrBGaW88h/rme5n4+lEAlIYGAlu3gqqSP3KkqJViYMd15A6ttIoMXn89hdOnS1ovlkMJa+C4KLqCPS9Ps0cz6N0R7LkCemtoXecVrz7DQO+KIE23rI+4PZVDbQuhhjUQYlG+Yk/nvCJSIbBGlibygZ1NGINxZMHB2NaALDhF5TMLiKC66BQlKT8Z1DrDXsZ/gfks//LC21nNawAAIABJREFU03ITAjfpPfcipKF3h0GCm7ERARUnbeIm1r42SlTHtVwozH8eRMvXCxRjR/ZGnue7le8g8WwZl13mE+fP0rntuurO62fPfXx8Nhk/QK8SezrH9D+cWPEl+vNMPYNzoGaNajm+vCuM3GD2HOClEhnwShguUwQ6UrAYLVjsCAc4la1OihNVBOlVMpqKn0k9CuEmiLRBbgYQMHYEzPnAMz2+7u6AJ1kRq/RJZsZzb1mNUaLt+cgz0HMQLj3nbRb03kOBXbtQGxrIPrP+hMPNedei3tWF1tONLJjkjx0DdwOTPl3BTZiYmZVB+EKAag6nFl1KiiFtr7BSCWk4aQvXcdA7w1jjxWUw0nRxJnNFQ+fFAH++VkXrCHs1HLb0eigYCkZ3FKGtoxOr9u1VbPtVc1yZdxARHZlZP8ssczbmUAqjL4YIqjhzBdyCjb4l6gX9I2m09hBKUEPaLirU7kCjgNumMOFcRBnScN3KXGjqpRDy9ec+Pj6bjR+gV0H2xUlmv3K6qB+xT2VIy/UycsNJKkjwVYTdEeK/hOqTPU86Li26yrRV/eB6gwYXyjQ6coGU7bItFGA4b2JVOGGRQrA1pLM8oqr40bbt8HzPExcr3WMt2RnPQnE5QvW81RfsGxcINpQ+zsw5aNsNk8fRFC8ra42O4qRShG66idyh0pp6xTAwBgexRkexxsaKbpNo0olWI3Gp4ElcLtEohZQSpcFAdeadUGpFXRqQCGq4l7Ned+HBOEhPjuNYDvqWGG522eqWAK0tjNCVdd1PtNYgIqzPB6oCZ27tRFEJqjjzsh4l4mW2ywXnKw8gkI5EhHX0uIF1MY3RH0fviiCC6mI2Xu+NonaEUUMabroK7/mIxkmeIz+T5vipJysfF6XnL1JKhKIsyl7Wo21gKy09W6o6r4+Pj0+1+AF6BUjLZe6fzpF5unhQ4FM59mQOJnPovVEvw1aHNuif3xmCGnzPS9EbNJi2qs+kT1s2DapCoozX+ZjpjfW2hkhFcheBV4SqC4ErvQDuLc4wN559tPROvbeConorFk4d7B2LpR6l4wXnW26Di8/geW+GILVORr59N4y+AF03Ehx9geCOO8mfOo+xpZfcoUMEb7gBZ2YGa2RkxW7G9u3kzp1Db2pCFoqvPojuTn4t+B8I7AkCEiklrpC40kUiuTt+J7/z7FtX7ONW0ZSoGNJ0kKaDMFTcgo09mkZpMDxP8CqbcilxA6EK9C1RL1hEonVHwXFXSEyUiAYqK7TjWnMQuwLHJCVmrCtXWWyYNo+bsdBaqysUN4eSoAqM3uiixeTCMdXmpdoHaySN3utpyN0qkh4yY7ODG0l1VR+gl1rBW/BIjza3kJ6ZXvcQ+9/wxurO6ePj41MDfoBeBmsyy8wXTmDVqZOmj4c1kkZtDiLCsuomKcsxu8N8Klib73kpQkptVjNpx+VVDRGeqVBjPlooHhy2GxodhpctnzYdmnWVo5k8IVVhIQf4qWN/jJKbXbbXvEd9322QT8HIT5fu6r/Tk5awsPu80HjiJNiV2mCukxW++DR07IV8Euy854NejI59cOEp71iXTyC23EqPOsx4ZBfZ4+cIHbyJ3HNeBj14/fXkX3zRe2ShEDKbJbRjB7nnnis5jAu3biErnicrl8my5od9b+Mv8JvPvam2LpeKWFeHrQRUL2s+H/y5CROtNYRdTYCugNZgUDhdvnmOm7FRGyUgUCI6bhXZbTdV/JrTuyLYM3kv+776pa7y7aB1hD0ZTpFLxlmlnxcBFfN8oqbXJT4d5213/ltS7iyHTn6H6ZmV1128vZN4Sysjx4+xMBixWqa1CiNYfjIyeODm6gfr4+PjUyV+gL4OmUOXmfvamYot23yqw5nJo2+JYmVr1/P/7XXBumbPN0o104ThvMXN8TA/S64MkgdDgcUgv1FTSc8X0h1OLWX1c+E2jNmz3h/9d8LES9DYB8NPrz3RhR8XH0DjwFrZSknKPLLsLKRGS9/fuhOmz7IYtcU6YfR5jNbt9O38Ie4OncnUXgpNTbizswh96aMpsH07+RdfRG1pWXcIjw6UdrV53wtvJmga6z+GEphDSUS4dBdQ6UqskTRKXMcYiGNdzlQmnYkbaE1BUAT2VBbzYmXvAyVuYF1Ke43O5jPUbsFBbQuVtW9VIjqapqBGdeSCFaQA15bgSqTlesWe7aFFi0e52pmlDAuNlcphDMQ31FlYmi4uDj946rNF7w+EQowcP0r3jt1IKZm6OFT2mKq2frFqx9briLW01jJcHx8fn6rwA/QiuKbD3NfPkn3u8tUeys89Qq3dGL3QG+GzgfpmzwGmqm33vgGyq+QwB2JhhnJLEo65EraM/27wA3xM0Wka+TFiIQDPzUJDHzT2woWfgB6GaAfMnl/asWlwSfpSlYynzHNcrvouEAN72fkSF6B9D6QvQ9Mgyux52uLfw9z3RtJP/JT86TMYgwOgqCjxGHpfH/njx0sff2sfPwmVyNwDcqOXyDoLCAvXsJu0MJMWqMJr3tMbXZGRFgEVvSuCmzaxEwXcpImZrF5io7UEkTFjMTgHcNMWRgUBupz3c1f6Y57bSt7xrCTT5qLDkt4R9iYlEQ2Z2aT3giYqs6ctQ2Bc48EDH0GqkiOZxzl+/AkAuq7bxdjpEwCkZqbIzs0SbmgkPbt+N1rXteneuZvRk8WvtT2vqawBlo+Pj89G8RsVrcIazzDxyef94PwK4W7AdvGvtxv1s2VYxplsgX2RKn3C5xkuUyS6mpcyeW6MLS2rpx2Hy2b5wOVraj97tj5CtuPGlXdE271sdvse6LwBEpdg6z0w8Grovwuy0zB9BlKX1894V0ux10ENeBOEjn1eIL6IAr23eFn/7DSkJ6D3VhRMAs0KhELIVArz/BBThRkKQRU3lwO7+PMimho5+qqOdYcnxcZWweR6u69uUuVIrEtprJE0IqxjbI2jhDXUuIE5lMSeyoNVeyGpkzBX6M+rwRqbd6e5kALh+bzbs3nUqI7SML/CoAiMwQZkxkbvWubIE1BRmwI1j3sBJWagNQYq0syXxQU5Z+HqLsePP0GkqZmu63Yxd3mpXig1NYlj26Smp5gbX/+anx65iKIUXy0RisKuO16z8TH7+Pj4VICfQZ9HSknm2XHmvnFuRftun81F0WoLsHN9Uf5nYPMy3cEaM/uTpo1CdZLa5Zr3DU83pPScUjRjqVlQfg5Gn1+7nR6eP6lYdWax7E9R4SSoyPPVezNcfHZVcD5/+3KNvJXx/t7yKtRhwHGYva6Dz/9qJz8pHOc/ncgzMDmJc/0OtLFp5FxiKVjfPsAH35pkRFv1+Fax4Qz6Oil0e67gua8UcW+RGQs3a+DmbJSW2iZ9aw8qsSeL2Z9W9yCdnIXMWAhD9ZxW+mLQFERmrUWbSGe+ERMS3JztBdXVXuCrhigLDnYJLXytKJdd/uUd/46Xpn5cfeFohQzuP0i4ocqGXT4+Pj414mfQATdvM/PFk8w9esYPzq8w5oWU1068Sj65rbbGJpVSa0dRS0puiFXneuFIyS0NXqZysmBxW0MJH/FKSI16WvSO65fdWOSxCMDKej9mBsy099M86PmjFxZ+kpBPrPVAX3O8VecIxDy3FrdIIKaWyAtcfIZwfJqzrxnkw79i8mT+GK50mYxK5I5B/vz1eXBd/uD3m8nedSMiFuVj91uMaOW7eLpig/776+zuJk2MLbGS9wtdweiP100uosZLZbGre4xqWMfN2DiznqTKHE5hDiVXeLi7aQtzKIl5IVmfjLcErS2E0R/DGIxX7RCz3nH1gsbQxRfrc7wi7H61L2/x8fG5crziM+jmSIrpfzhR/4Y8PhXjJE0IKEtdBcuQGYjxJePK6cSrpVK7RYADsRAnMnlSjsutDRGeS2QWavMqQq4OvpsGPJvD6bNLt1Uz2XBKPK/lDrH6HG17vMZExSiUdrmZM0b4968Ca1nr9bOxDJ/7v6Z4+MQu7O4AZ/TzvDS4BeeGmzgc+EmZgXlsXINeOvg1+uPrdve0LnorGUq8tiLVNcxfIMJQ0No9xxR7Or+ufeJq9J4oTqK6Zln1YrlPuzEYh6nam4MtR845vGb/O/jeU3+zoePk0il6d+/Dm/B4z7Wq62y7+VUbH6SPj49PhbxiA3QpJemfjJL49vmiS9M+Vw43ZaJEdJSogV3BROkvtmrA5gboo4XanWEu5i0OxEI8n1oZeNzaEGYoZzJh2uwIBzAUhcOp3GLe86fzzi2rJc2lCAiBFe+FBTmOokByFOYurNqymojf9YJr5FLWXAiv+ZAWmj/UsuMJ4d1uF6C/29OTC7V0cA6gldYxt84MIRoHV9z2aPw0AJNxyWP3eGP6094XuKn9Jpio8GFtUIO+bnJaLLW7X5dKX9gyCF2gdYaxL2dr6misd0c8LXodxqN3RzzJSrH37bzzZymMgXhF7/dKEU0al5Orr/3qmb649hj77nkDurFx/b2Pj49PpbxiA/TMT8dJfPPc1R6GzzxuxsLNWF4RmgBnpkR2L6qzy1Q4qKg8p9ibUiQKcCFvcks8zLPJ2pb1n0/luCUeIu1IVMBQFX6ayNKsq+wMB4hoKodKHPulTL5ogL+auCpoOvWN8oMp2mSoZE9FmHxp6c/2PXD52PrH77sdxpZpwBv7vUZJy3Xmy5k+C4oGRdqz69JhS7ids+m1jixf6rzAOW2GhQmC5VY2idoe3UY0vUH9d4UdX9elTgG6k7axx6u/Lo2BOIj5DPYGxiI0Fb0ngpuxEYaKPZNHieogQI0ZuHkHNapjT+dRmwIrnGzUthBCSpy843UTrpOiMNdj8o0f/2l9Xqci7HnN6zbluD4+Pj6leMUG6PZ0fZZVfeqLM1tA740iLVm8qUra4u1PTvN2gLBGuiPE+SaNn0UVvhOwOKfU7wta3WDwn7BdzmQLK2KQGcthxlrfgSNpOwznLRo1hbl1aiKSjuS33/ANJIKHf/ZhOmdPFN8w2ABtO2FuxCvIXI/VAY5aQ9Zw7oL303kDWHmYPrXy/ty0592+2p891glNW+nUopxlLWf1WZZn76dz63d8XKBNbcGwN/ZRpzYE0JqDnmuIlIse4kJK3PzaiYYxGMc1XYSUIOf3cYGNWgtqAnuitqZpTsYqa8NYCdJ01shpJN417aa8SdNCQyJpOmgtQeypvOd7PjTfUbQpQG0+NCuxuiXPX3qM808eqsPRihNrbaN3195NO76Pj49PMV6xAbqTqK+LgE/9sEbS6D3Rkl0PF8naRM+nuP48XA+8G5ANBrMdQe4d3HigfiiZZU8kyEuZ2pbhT2UL3NYQ4ekKO4suZ9qyy+5bkJKvmA0AjN3yKcLYNLs5/uxHD2I4y8acT8LkSe//TQMQ6wIUGC7WwGjV86ZvoIhv/Ij3u+8OGF6lFZcSem6GSz/z/u68wfNrH/4JvS1vKnvoqB5lNFOZTeReZ0fZbYy+GHJhMrTsKZDMB+EFBydhYlcY4Mq8gz1W/+7DekdkhYa7EhYaIjmpK685l5brBeeDcXAlWmvQk2K5LmpLCDWkgSKwJrJVdRSWHSrPXf4+Z3/8s00cvceeV78OUWN3YR8fH59aeeUG6Mn1v6yMwThu1q64K55PfXFztWnARcKkOWHCQHTD8hdTSsYKFgfjYZ6rUurSqqt0BQzOZ/PsjAQIKypzts35XOUTw2SJJkXF+ElBw3s7B7ntpj/knc8+XHzD2SHvZ8FicTVrJAIVTHScMo9p+szKv1UDUmPeOBoHvAz/xEswL1kZofjxAmoAXdFJW2kGGwZ5caoyx467hvaV3Ua6Emt0/YBa767cXccay6zIGNcLESjd0XQNhgKmi1AF1uVM1R1B60mpAtbFEQnQt8RwUybO3DqfzS0ax7PPcOTpx+o+xlLsvuvuK3YuHx8fnwVeuQH6bOkvAa09vPiFojYFUOebarib1VXPZw1O0gIVal0H34hV83JmbYfnktmqM+FxVeXFdI5bGyIcTWVp1DViqlLVQxorWNwUD3EoWT5rG1EEmhCkHJe/jd7CO/vu8CwOc8niE5WSk5caAvRyRaiZCQg2en7sRhTad8PMee/Yc0MrNp0JN/F0YmVArwqVG9tu5NDEIQpOgbZQ2+JtL0y+sO6pt0W30nE8XsFj2AQUgTEYR9oSIbxn0hpOld2tGGpjACWkFXeLWXj6JSgNxrwUx3vdXMvFLjPxuCaQntuN0BXUrRFS+Sl0gggEEhcLk6nsCM8+/y1s58qtBLT2DdDS23fFzufj4+OzwCsyQJe2u67FmBJZelqc2YIXzAvQez2/7uVFTz6bg9YUqFhOUHR/KJGHrQ9BIcivU5B2qWBiCMGpTB5XSmKqwulsgVsrDPQHQwY5x0VU6MDSHTQ4nS1wQ0jjT0b+10pJidm1dgcr5xWAKqrnuiKU+f8rEGkHLehlxgsVZICzU+W3ab0ORp71uopefNqT2hTZ99mevTj28OLfcSNOV6SLQxNLGuPJ3CSTuUmua7yOA+0HFm/P23myVhaJJKAG+Mjcb9F2PobaMp91liBUgRLRcXMWbsFBjRg4KbNs9hzAqmE1bXnm2BiocaJgKCghDTdn484VUNtCqBEdaTqej3mygAipqBEDezKHuUy+p7WHPdeWayhIFwF1sUPpihUGVaB1RsB0eeLol5lLjF+lES7hdw718fG5WrwiA3R7Nl99gC1ZtDQTEQ29PewF7+stx/rUjD2Zw+iP4aQs3LxdlT4VwJACc3MMXgDoDRmcyZZ+7QsSbmsI83Qiw83xMJoQuBR4OpFhbzTIsXRpXfuBWJgTmRw5VzJulteiw5JT6KutYQ4c/dzSHd0H1nYRBc9OceKltbcv0H/nWt14MbpuhLEj5bebeAn674ALT3l/zw5BuAV6b/HkLgnPtSXiLq0vtIZaMRSDk7MnSx72+YnSHUSj2QBiysJhlVxqMudlnRWBO1fFNK5K5xNzeO3kRmsPo4TnP3aFlyxw8876xZumi2u7qK1BnLkCSkBdI51Rw7rXT2AV9kQWrT20KXKbWlBbgihBDXMkhRLS0XujuGkLtcHAmsxhjaU5F37pmgjOAQYP3Hy1h+Dj4/MK5RUZoJcPqteP7GTGXsyMaZ1hlICGNZpGWn4X0npiXvDkAGpjAKdgVyV30TYxON8eCjBhlp8wPJ3IcEM0xM9W6denTJuAIigUCfjuaIyQd1xyy+77WTLDloBOSFVQhcAukrkfznvBWVKsboZTwxOhBctbKy6g6lQ221Vgdnjlttlp7wegeRtEOwggCKpB9rbs5Xzy/LqFoHIjy1iSqvsfiLDmdQM1FLDckg9b74shFIGTNBfdTADsmTxCgLmqI6cSN8pmuZ3JHGrcQN8SwxpZKZPRuyJe86L5AN0Y8AoyzXk5jT2RQ+u8Nooc3aTprV7ankvTQiG4M+etUua6Cjz74wqsQ68A0ZZW2voHy2/o4+Pjswm8MgP0Mh303HTlWbVFP2JDwRiI42Yt7AnfwrGeOHMFL/MW8iZClYjL1XJdUqpk1rIJCugPBRjOm+RcWVG30JG8SZOmMrus4HMwFFiTETeE4IZYiJ/MZbi1YWUxoi2hUVMZLlgkyhSOSqF6Li2pMQi3wtjhKh8p0HPQ+z19xpO4KBpFA/1l2W4i7ZCZpORz3nodjK5jhTdzFmbO8vje1xF0gjw38VzZYcpN8rwuiq4g8w7GYBwnYeIkC2jNIVBY4UluDMZxZvKoTUHUmLEiQC/VzMhNmqhRff3zK4ArkbaL3jnfaGgeJ2N5n1muV8hqDiVBEyhR3ctONwW8VcNVCENFWs4VketprUFEUEMoAjdjFW1QNNx4lqd+/JXNH0yFbLvpFsQm9Vnw8fHxKccrNEAvHYBrrcHatM+mu7iErLWHsSd895d64kzncfACoEpamutLXbo3zK0NEQ4lMmwJGZycl7XsCgc4sY7EZYEZ21kjUYmoK7OZgyEDTYjFTPtPExnaDW0xS99ueG/TmKqwPxbip4kMpitxgetjIY4sa2gkpesF59EOaBr0NOXTZ7xCzYoQMHsBkvONgmLdkFqVxW7og8S8Tnz0Bc8rPTvtadqlA5Or/Nj7bofhp8qe2Ym08z+yZ8pud1WwXBArNeWefGSlxtuZK+AkTNSmINZEdtEP3R5dv27Fni14nz1TxaVPek8UeyaPO//Ztfx9oMYN3KSJ3hnGWpgQqEsBupt30BoDniOVCsaWONZUFjVmgOvp8qUt+f/Ze/MwybKzPvM9d4sbe+Reude+dFd1VXdXVXcLiaYFkrFYbIMMsgFjjIEB7BkDAgbm8fgBMTY2Y2Qj8egZzbB4DGPZYCOMJMACY0ndLXW3uqqr9659z6rcY4+425k/bmRkRGZERkRm1tLd522lKuLec+89kZEZ+Tvf/b7fp0UN/LwDfoAMwBiw691AnWv5TXdcri8QOtwBK5SXNnX+O8XuR0/e6ykoFIp3Me9Ogb6BxaKWsKDNH8luqeeYQlhcuiOOe6v4zi0sFSDs2mteG9Vs9JR2/S1bqzjX8mhpqy5U2tEhHtkzxxtE9i7b4rbjcShu80YHj/TxiMmFmh+6IHSFeSlf4j2ZOIGEWcflYgvrxUEzFOjHUzHeLFZ4xQmvk9D1pvSXRcdrbQNZuB1+AaCFnuO6GRZ+umXwqqG9oWmvvkd+NbRfvPyV1fNUW7iONC58Grt5ztbSYsYfheIClBfDyHkX4hxgcWAauN1x3AqdUlyWogViJLs+X0c0sU6krizEzfEEwtKaBLwsr6bC6ZnIhql1suzhSxk29WkRXdYsHbfhZ965lMOaTuJcyyMsDWHpBE4AK1aK1QCvtkBwLuXw3CAschcijMSXPUQqgnt7deFoTiTQ01YoyC/ncPINKTM9iHNh65jDsdBB5lYRYeldpafdT9FqIxJh6sGj93oaCoXiXcy7UqAHa/yAI/v7QteQxQru/DakpzT8nTHHE7jXC2hJE2Mwir9YeXs3SdIFetJCWHooDAwNP1vd0LayERHT0aMmIqIjTD0svBOtOnSvhsCFqKUz1MZoUYMgYYGAoOTiL66/9gccg9+2N+elvpZl1+NyTUSndI2KlCx5Po6U7I9FOFuLpD+ailENAl6tFYBO2SYlXzLvesxlw2j4SuLNmVyJlGEw47Se4/WKw/FUbF3+esbUm1JmrlddfrHwP5iMP8RzMs2gm21xtmC1IVAnBg82P2+VRlJpdY0GbrwIA/vAioePu0QPgtBas0sCufFqzxPb6/ttDEXBDcL09cUK2gQE18J90gsQVsOdkTVaU89E8AtOmK/UBlnx8X2J3h9p+pm2dqXq+eSNOFfzGCMx3OsF9KEo/trAQrAi5FM4V3L1IndzMoE1kazXeKywsn8FLWmhZyJhcKFLrOkk7mypPl8taXbdS+J+EuhTDz6EYa2t51AoFIq7x7tSoPd/7wHc941TemkOayJB7NhwfZ90AwrPzZD74hVkdZN/4H2JUbMR82pRsyDv4tTaYBuDNlrcBCHCZkiL5Q3/cHeFAHQNoQnQqP0bfgkRbqs/rjlYIKg/F4ZW3wbtG4tYU8muUkzaIUs+Xmn7hJM+3LrT5Q9cc/ntfdtzjRUBLghz0F8phIu4oh8wU3XZG40QNzRezpfRBBxPxZh3PXKez6Lb/FpX3uViIJkydW477rqbCkcSUWaqzjpxDmHh6dqI+d945ZN8Vy0NxdW2ICqGH2jh7LK2s2gCqh06WUaSYcpLebGny6eXrkKb93Mz/J75WZJHEwS1/37q2vcjFjffy8C7VQJdsPjePyJrPsdI6cPEbh7HmkyCDEW6nrbwc866OhTnci6MsptaezcVAVrN71x6EqREz9irBekjsWaxKyAoeWjpCLgBWtQAW28OAFhauDBovIyh4ZdchK23bF6k90fQoib+UgX3Wmffdn3ADtNsSu460R/ku18kd2spqpsmvrs9i+92jB988I6eX6FQKDrxrhToQhNYE0msifW3v4WpkXzvONEHBwjKHnrCwlsOo96VNxcpnZkDb+PIXatoVyPefKU5jUaA3m+jJ2uivezhL1Y6usIIS8McTSBdPywa84K6nNpqNo0+YIcOC5LmedxnRjX+bBktadaFgDEYJfUtUwwkTH5GlPnD2WWuVLZ+x+JoMooAXso3C6+8H4DjUq4E4RpLwsv5MkeT0XrUvR1vFCs8kYnz1eUwQjloGuyKWsw5LvNu+0WM1iBkjskl9IYccTPYwms1WonjNaJJE2Ge+UYMHQw9z3tEL86x13iQ8153zXw6FYk+7T7f9PyfaN+3pbIELakzc+LTLBthCtC1xCfY/+jHcZ5fnYc1mUCLmy0dWdwb4cKmneWhiOjgBbhX87XfPzcUyJoI01nWLoyD1cJTcyqJN5tHxAyMoWi9jsYaSzRfq3YLx58rIyI6+nCMYKn5s0ZPWuuE9kboCWtLi/YVdmeOsvc9j/BXb/4eC4vX247bd/Axxs29/NWZ3yPw70zzuN2PnLgj51UoFIpueVcK9G4w+mzoCx/rqTAqGTsySOY7doeFYDW7MG+5WrcK85arOJeyvdstyvCWub+mS6CWthARHc3Qwui4LggKDoETYKQtnJsFnCt3xttYixnosTCS586VwJP1W+UbET0ySGRPBj0TQZha6POcd/EWy3izJbylKtZUEn+5inMlR7DG39wYCX2i/YUKfsGte0/HHx8l9vBwGO3XBHqfjZ9zcC5nw7bqU0miDw2hWas5Ej9LHx/dPcqLuRJfmMviS4mta0RrXTf/8+2ljjnkK1wpOyy3cVDJr3FycaTk9UKZB+I2r3c4/3PLRR6M26QMndO5Ei/kShyI2bDWu7sBt0Eg/013m4oq01NwszkdJdAN3OGdaMvX0Iw4QugIpwjpccjPIhryz71InOL4LpKX30DTNx/F/yZzsGuBHvS4WhT+1lIogrzPjus/gDe5TEF/BYCz6Z+i7/1Pkim8j8hrB/BzTngVT+svAAAgAElEQVR3rA3WzhR+yQ2FsqBpwSs9iZ6OEFQ9pBsgHR8EWJOd71oJXSDiBkbGxr1dDFPrbhRwZooYO2J1pxlrenVxIMs+fqW0fjWv9fh92qbMFPOmBkge2P0+zrh/QS4/t25M38gYD1ROYhZMvvHY3+WFC5+juNzbnZpOJAeHVPdQhUJxz1ECvUc020DbYWDuiLfcL/0A50aBymsLFE/NomciyIq3KWeYlULIRlko4iZGv41zs9CTL3ivyLKHjBh4M0XMiQTeXBl3duNc1PS37yb53vHurxHIsGFJLHxN0gsQplbPRZWuj19wkY6PObL++63HTazR1u/DCkIIjqfjHE+vH/fjU8P8wa1FPn75dscou9ljfmwxkFwtVzkQs3mr1F6kB0DJ93mtQci/VaowGjHRCXPM1xLVdB6I2yQNneNXLrQ8b7V/At/Uid6+0qSfJBBYUaSu49nh9ySwbPwdhyhqU7gRi1JUJ2fmyVcuIbkFmMTjuykW3yTMlapiyRFsa5RSsAAE+H4ZyS2iuw+zP9fHwJXN6bZH5J37SPrtqT/mO4bez/DF2KZTyuRZi/GzP4P36DWu9/3fVLWrLBlfYinzJQ5OfgoZsfDOB6CvLygFkL5EVnyMoRiapSEJF/bmYBR3rrQa7Y6JUFgvVbtahHvzFYx+G6FrYdT8er6+oPZmS5iTSYKCgzPT/DssogZaykK3jfq1/YKLtTOFdIMw/7xTgeg2p46PLUxRnD7OqVf/FE3XCfzVD7pHx74VczlcAI0sjvKhvh/mrZ2nefmlv9i264/u2X9f5cMrFIp3J0qgbzNC14hMpYhMpUh9cGc94uveLlJ87haF52Y2bVcGIIsubnGL+ZeGwOi30WImejqC9IIw33S2VBcujXZv7o1mizg9E0GLm3gLFWQljIBrKYv4yR09TUNogsjUavtzYTVXCApTx+jroWqwR3Qh+MjoAN+7o5/ns0V+9dJMPd2kkW7cWlpRCCQzVYc90QgXyu2LaC9VXE6mYzyfXc0vnqm6PBC3ibpek2sLwJzr1buY2kuXmvY5fbv5w30/hD1yi3T2P2I9uJ+InsaXDk6Qx/MKrIZtQ+FjGDq+fwYp3dXNaxZ/QjRbQzqiAqKM5zeLx7Jzg8sjO7j4gcfYd8Wh72z7Tp+t2FMudS34ym6ZdCRNttqhaLXGHzqf57P6n2PtM/l+67t4T2yclMgBPlIEhMaVQfhY+ECAkAbJF9+HLNe+IQK0jM7F/l9Biub39Nzkz+KLAjvtXyB563jLNJGVnG4tauDOlZFVH3MqiXM9D57E2BEDwnx3r4fuucaAXRfY5kQCczSBczOPtSuNcymLey1Mf2FNXY0seYi42eQw48+V651NzclkV3no24kwNeKJPiLxBN+y+++xFJnj1Bt/yo7xfQwsDzWN1dA4lH2U/kd38OWXPrMtKS8Dk9NbPodCoVBsFSXQ7yBCX1Ua5kiczHfuIfHecZb/5AKVN7b3tmw3aEmL5JMTxB8dCQvK1iB9SVB0cW8Xw9vrCKqXs1TeXES6AfahfuIndmCNJcLxUuLNlaleWMbe19eUXvJ2QgjBY5kE//nYXn7r+jz/x8WbVGqieJdtcatFFLtbcn5AUHV4LB3nuWz7OxBzDZ1Jd1gGw5bJq4UyQ5bB0WgEJ5Dka5HEcyviXBNUzBhBtJ+v7f8Iv5V8D5/XxvnB5Jt8qPR7eIDjLeJ4G/+smWYGz+uQQtFjmDRfvcCpHTA0/RR7Xr1CfOZiV8cNZm9BprtrWLrFfHG+p3l5tf8+7fw+N/r38gHz5Y7HDDx+maFnvh/pBcw9+fssGl9suYjwRZhjfjn9L3ig+O/WD2iIqjcWewYFF3M4BrqGd6uIORoPu5Hqol4DEpRdZMVH77PR4gbOTBGZdzEGbaQQyMa6GCFwbxXQkxbeQjmMpF/LIdsJfl0gdANYv4h0r+XDwte75DylD9gIU2Ps1iTfeeJ/QbvikSgkGRn/UQLdb5v5NbI4TjSRpJjdupf64KRKb1EoFPceJdDvMka/zcDfe4DSC7dZ+q/nt+7e0iXWrjSDP/gAmt3+LRe6QE9Z9Zx7gOiDA/Btu1uPFwJzOBaKi3cAmhD8yOQQ7x9I8o9ev8rFUoWCHzR1Ad0MhUDyXLbII8kYrxTKuC2KG2eqLgfjNkld41SuxK2aYL/teNx2WgsrUwg+dujneGv8f2JZRAD4yeSLvCf3z9nu0jnZk0BfHTtXfYX5/QZjhz7ArhdPE8luLKjNpctk+vawLO+8ICz4bleG+Qvmf0N/Ik2sso9F84udDwgM5KzG2tsQejqCnrRwI3Ncn/wE4zM/Aa/HEJaOe7OInolgjsYJfFlf3MtAIkwNTRpoA1Gq55YBMAai6PvjYe3KUoWgISXDvZbHGIrWc+G9uTLGjgT+XGldfYy1KxUuzAtOmB+/1GwDq/dF2lqo6v0R9HQE53oHV58uCAve4013HaySiVf7SbZcE9yN3yzd2J7uByqCrlAo7geUQL8HCCGIn9yBPmCz8P++vnk7x3ZoAnM0jjEYRbN0tIRJ/PjIhuJcscqemM1nH9nLv7l8m49f6b5xTidO5UtNri0r9Js6e6IRDOCrLawVW3EoblP0fZ7LV6EmzgECLYltT2EYCXTdRmAAkkA6BEEVzyvhuvP4fufrJJOH0fUYIBDCJJN5rGm/ECaOc6tpm6ZFKRbPNW2T0uOGd5pbD0eZ9r+FqWe/gu63Fn0CyZPWMH9cbe/iUX+tW7QUShvdF7PORv4AIp3HGcEA+87/GsFsC/vClIU0fM5N/zS+KPLWxE+wa/B/Rbx4GHMygXer1LaZkTFgU23wI/cWyngLZdDAGFzfudibK8NcOSzUdgOCoos+FEWWXIJiLS0taTYVn654rxuDNlrSQtasG/VUmAa34kKzgjD0bXFvATDXus1sgm8e/LucHT/DG699ZdOpLrph0LdjbEvzUCgUiu1AKbZ7iL0nw/BPHmPxP7wZ2iRuFiPM5bZ2prD392GOJd626Sb3CxFN4+d3j7InFuFn37q2Lg98s3xtuci+WIRzpSoacDId59V86N4ioL5vI44lY7yUXy+wBbDX+e9UKlc7zsM0B7CsoVDIazaaFqNUuohsiFzreozl5efbnsOyRtZtSyWPsJxtfYwflFlIa2SfOMCRNwroC63TXh7Tovxxx1fQ2WaxEy8u3eYD0wfxS29u6TwrxPxDTL/8iwRz68W5sLQw0vxAHl+Ev+sD1gcx/3I/5mRsQ3GqD9jhg1brkQC8uRLWdJKg6oe2i7VUmqDkNUXM/bkyesaqWy0GeRdrVyrsHHqzAE44ttEG1hiM4s2Xw3Fr8GZLbS0je0LQ1NF0s1hOhMPOSXYfOswb/nOcf+N5Rvce4MTf/DC3L5xj5vxZbl84R7XU/lp9YxNouvrsVCgU9x4l0O8x5nCMoR97iMXPvEXlzd7z0hNPTpD65iklyO8QH97Rz8G4zfecubCu6dBmkEA1CHgoESXn+3ytIS9dAq6UGKJ95tMjqRgzldaJuD+dep6RbBcpGIDrLuC6CwDY9hSVylWEMEgkDmHoSarOXM8CWAiDUvlK2/2WNUQu/zpSq/DlB3T2Vr+RkZkc1rWXmsYdbNNddS2bEegDdj8LlfD37EYlx0+dzfMLe59goPIcWzH5j2n7mX7pFwmWArRBnfKe1/CNIppv4xtFbkX/A4PVb6VghI2g+q2nyFx+EnMo2VbgWjtTeIsV/IUOBcqSemqIMZZAi2j4RQ8qft2mdAVhaE0F386lXM1Wcf33UktZeCudldssUJ3LuSYbx57RRWgjuVWR30CsGONRnmLv0YdZHllk34kn2HfiCQBkELA8e4vZSxeZvXyB2UsXmL18kVJ2mYGJKd7/Qz+2bfNQKBSKrSC2GoW6Exw/flx+/etdtiZ/hyD9gOXPXqD4wq3Og2vEHx8l/cFptNj25F4q2vNaocyHT5/fcj76Cu/NxHm6hWMMwOPpeJNwzxg6B+JhFPWlXJFqm1/ZtKHxeCzPAXGex5Z/ueu5rAj0tSQTR8gXXml7nBAmifh+VsSdYfaztPR02/GZ9Ml10fVD5QcZe+FLTdsKOw7zRLSzYBuKDrJUXSaQAYFcFdd/bewoX549S9lrtjZNWUn+6Y48vojwVf8B/vj6qsPMB4Z38TeSC3hO979/KyQTD1AtzSM9Sb/7zcybX8DXmudvmcOM3fyHFEdfRgqfwae/D03obVNagNADfTqFM1OAam+LB2NHHO9W658va3ca5+Kq842wdYzBKLLsoSXDCLv0JZqpUb0QjjPH4i2bL0EtTz1bXbe+aWwgtu6lmRrmRDIsSG9TvNrYcGmzRPb3MfQPDm84RkpJcXmJWDqNpqlAx7sZIcSLUsrj93oeCgWoCPp9g9A1Mt+1Fy1lkf/LzikKwtbJfNtuhKl1HKvYOg8monzm2B6+89Q5qltMd9kZtZhtU/gJ8EK2yK6oxaWyw9FklGtlZ0MHmBWyXsCf5+Ls6UvzqeRneER7g8eyv7SFmW4sCqV0yRdeqz+Pxw9sON511ztsVKIRZo++BwlITeBEbSTwj+1pLE3gSRk2gpLwn2dCz/esG0aUpV/i41MBWRknpw3x5aLN12Zf5xusazw5JnnaP8af33wFv9bY6UM79mLKZzBlifgaHfbF2UtE9L18i9GbQE+nT5DNvggEoMHtyGdajnPcWbzUIv1f+DDmeALfreB3SGVC1iLUI7Em15dO6JkI/tJq1N3amQobq9UaoTkXs1g7U7g3C0gnQFZ83OuFMPVlJVovwvOsEJTb/7z6S1WMoSgioofnIbR6dGdWGyY1oiVNNEvHudSdPeaW6CIAJYQg0dd/5+eiUCgUPaAE+n2EEIL0B6bRLJ3sn17acGzyGyeUOL/LHE3G+NjecX7ubOcCxlZYQnA8HeP55eKGLis+ENM1TqTivJDrLMz3xyJENY1bjoutaVxhN08XAkbS3TeN2h42FkN+sF6QLmUMLnF23fY9Lb5BR/YcQyu9im4OEegpKloaKq+TCG6TCG5zIPoeLkYHAZ+YXOSD2rM8Nj3BF8tjnFq4yMOsWioWW9wI+fzMOfJDh/hb9hsdXymERbTZ7Asdx0XMMTL+E8SXD2PtquVs97DG67Uzsb9cBV1gTiXrIh9ARPR6QbpzOYeWtDDHbdybxXB7w5ys6VDUr+Sr+0tVsHWEAFYcY4SoP9eiBkHZq+e0u7eKaLaBt9ScnmPsiOHnHbwOaTvGcCj4t8z9d4NYoVAoukIJ9PuQ5JMTAG1FurANkk9O3s0pKWr8wNgAn5/L8qWl3pq3PBi3Kfk+z7ZJa1mHpCtxbgA5z+essyp+r9S0TwRn5VRUtWHsYLanORtGklislcWmrP8jpV93iOlMC7XUQ4qdKL4Udt50ZoAZBpIPkfdXo7MPB8/ycKjP66T963zYus6HxgeIBKvvWcaQPDxwgIVqnrnKEmWvjESQdx2wO89F0+JUKje6mTUTr/40xpVBABw2kWvtbyI33pe4V1dfr4jqaFETv8ExKsg7OHkndIJpsGUMCi5B2cNfrGCMRPFzLrIc5rSvfbdWnsuUhbCN+oJgXfGoCCP5a11f9HQtPWYNImJsT4Ok+zCFU6FQKLqho0AXQtjAlwlNxgzgD6WU/6xh/0eBXwOGpJTrTI6FEN8K/FtAB/4fKeWvbtPc39EkvnGc6qXsusJRETWw92aamiAp7h5FP+Bj+8b5+OVb/NHscsfxSV1wKBHj+WyR96QTXGpT4LmW8+Uqw5axYSoMwEOpGKfaWDM6mAQIPpn8j4xrWb47+yMtRhnEYjtb5qAHgUOp1F2DIQDTHNpwf6v26YHcfBOofP5lIpFRotEJCoWzeF77lIlYsND0/GH/WR6OAbFQw7lanLI2QCy6AwoXOl47mTxYS23phOT2Q7/DwPC3Y79wqIvx6wkqPpga9BhJb5pF2ccv+6GFYsLCvVVEVmpiPVi1ZVyLd7uMtTN0cAkKblg0uqamVMtY4d28WioS0NTISe+PwBpLRi1mYAzHcK7kwrsKDfu2tXup0ucKheJtSjcR9CrwfillQQhhAk8LIf5USvk1IcQk8AGgZdK0EEIHfrM25jrwghDiv0opX9+m+b9jEULQ97f3M/epM3jzZfR+m4HvO4Q1nrjXU3tXkzB09hs6n3xgGkdKPj/XXhQ+kopxpezwfC1//HS+yKhlMtOFS8mxZKyrvHN/gwjhH2YHeTbyX7hZCPjpdCi0E/EDGGaKIHARQsdx5llafIZodBfl8sodGxF+tRDUGyGEhqbFEUIj9E7Xmh63mmoQbK0hUbU6Q7U6gxAm6fQJ8vnXCILeHEWEAEsWsfwiGWOMzssu8LzubQFTy0+QuPEIfsxBaBpBocX7b+vhSsEL1vY3Qlb97bEzZNVC0ZpK4lztTgQ3Xlfvi6AlTIShhbnri2WCnIuz7GCMxhFNyl1gTSdxruRWyxkMDWsygXOjEJ5XF03zsKaTOJsR57og8fho7a6ODF1nggaLSoVCoXib0VGgy9DmZeU+sln7WvkU/jjwc9DWtvgkcF5KeRFACPEZ4G8ASqB3gR436f/IAWY/dYb0B6aVOL+P0IXgk4emuVU9z4trIthDpsG4ba2LbJcDyf6I0VagazSXZZrA4WSMa5Uq867PobhNxtD5ak24G8DV8sYC92bN23q68mXi8f0US5eavM5XkNJBCAvwkdIn/BXvLfyoaRZB0F64RqPrOzQGQQcLwS6R0iWbfQHLGsY0pygWe/c21/UUudxLnQcCppnsatyO8veRfPq9eJQxxxMEeQdrOkVQ9urNhYwBu56TbU2nQkG7BukFYGl1r/Itowm0uFFvWtQt/lJ1XWdRLW1hpCOgC6QXYE4mQROItLUaGa9dT+hac5qLL8O89SB8jY2dRHshfmIHme/Ys6ljFQqF4n6kqypDIYQuhHgJmAW+KKV8TgjxncANKeWZDQ4dB641PL9e29bqGj8qhPi6EOLrc3NzXU7/nY81kWToR44Q2ZO511NRrCGqa/y7I7vZGV3tSPlYOk4pCFo2EgI4ky9zPBVbtz2la4xHTCYitfbsUnIsFeN0vkTJlzySilHygybJ7AFLns+AqXMsuf6cjeSs/VQq11uKc4Bq5RZSOjVxvjk00XtJi+dt0j+7DY4zS7l8mXT6OLHY3p6O9f0c8fjGxyQSD5JIHGR5ubMNbDL5EOmFb6ivddzrBfysg3MlhzdbQkQNtLi5oUPKCu71AnrCCpsQbQPO5RxB0cMYT2BNJcHYfMF5UHBACPysg3utgNAFzqUcZsZG7w8j2Ea/jdBFS1tJ51IO50pundtL1+iC5DdNbHr+CoVCcT/S1V9UGf7VPiaEyAB/JIR4CPjfgA92OLTVX5OWYTkp5aeBT0Pog97NvN4tRHam7/UUFG0YtAx+anoH/+elGRKG3lVaysVylaSukfcDDAGPpOJcLFaI6RoDpsF01CLvBbxcCHOCS0HAqVwJQ0AlWB9BrfoBC24LkScln4n9U65ZjzPMPL7fWgxHIiNoWpRy+XJPr30dooPIa/Fb7XnrI6ZCmMgWuelCWMTju3HdLE51Frk2F4SV1xJDCIFhxEnED+D5RSqV7px3fL+977amxXGcORyni2JbKXCrS+QHTpGeeB/B9fUvXpa9nu5R+IuVrTUFaoG3IorNWurJTClMs+kSa2cqbHQUSPS0hb9YwblZQNg6zrUceBItHabFOJe35mnejvjxEYyMSmVRKBTvLHoKeUkpl4UQ/4MwTWUXcKZW+DUBnBJCnJRSNhoJXwca7UYmgJtbmrFCcZ8xZBnsjdv81WJ3t+cDCcfTcXKeT0LXuF31yPs+8yWfsOSjNY+m4i0XAEeSsXraSxNCkDMPMLb8OxvOR0qxdXEOnaPvrYpEgyICHYlPNDqF5xWIWCMUiuutDk0zTaGwkroiiMcPYhgxBDp+UCaffxXLGiaff6Uhnx7AJJM+Sal8EcdZV8fehOO0vntnGH1EoxPk8+0bNzWS9p9g7M1/iJdeRt5u3alzMwRFlw1bzW4WN8C53j6CrfdFkJ5E+gHmUKweenGuF0JBL0IbR2tnCukHBEUPv+KFufNXctAfaXvuLaELkk8pRyuFQvHOo+N9TSHEUC1yjhAiCnwLcFpKOSyl3Cml3EkoxB9ZI84BXgD2CSF2iTDB9SPAf93WV6BQ3GPeP5DiNw5N0W9259t8MG6T9XxuVBy+tFTgasVhV9Te8PgjiWjb6PyNqsOgaXAyHV+37yW5cRfFkDZpE1LUotE2yeQRhLDRtCiWNYIQNkJEEMIirB3ffDdb3VjJ59Zw3UU8v0AyeYRk8gi2vZq60LwAkBSLb5LNnmI5+wLF4gVSqYepVG4SGkatomkGrpfDMDJkMic3nEs8vhfLGlk7Q0B2Lc4B9JTJm7t+HD2f6NnHfCOCvHvHOgeLuNE2hUaLmWEqiy9xruRwLodf9Wi7BFnxcS7ncK8V8JcqaAmr7vnuXMqFqTTb3LpBRc8VCsU7lW4i6KPAv6s5smjAf5JSfq7dYCHEGKGd4oeklJ4Q4h8Bf074V+63pZSvtTtWoXi7MmSZ/NqBSX741csdxy66HudL1XpBaCkIyPs+5gauKa8UykzZJlfX2DTqwFgkzIFfdtdHsJdlc256OvUIQhggwvSSanUWKdtE7YVWd0SR0kfKClJCEFhIub640zASpNOPrhy8epqat4euRYlEhlcPkIDQw/3SRRJQLl+mUrlGpRKWrsRiu7HtCSqV6wRBlUhkgmp1fbpKEJTJ5U6TSZ8gkG5Tsadtj9aLRksdskOy2VPrilnj8X09F52W5WWkqHJ56lfYeelXuhbp3lLosIIQSNfHvbl+UWb028ikhax6oSvLNiGrAUITYAm0uImwdIShIXSBt1QNRXi1yxoFCUGuud7BuZpfZ6m4JXRB8ptU9FyhULwz6cbF5WXg4Q5jdjY8vgl8qOH5F4AvbH6KCsXbg28byvBUf7JlqosOTEUtLpUdzpaqPJ6O87WGiPiNamtnl5SucTAe5Y1imZIveSIdJ4B6NN2H+nnek4nDGgH6R4U9fKeRxq95hFed+Zae563otRwx8CsbeoM3Wzm239ZIqXSRZPIwlcp1fL+IlCCETSQyiK4nMIxkUzfPbO4lUqljWNYoltWHDNyu7SItawe2vWOdk8tG/uqtiETGKZevADA5/z8jJl389ALayyPgb5yaEuQcnJqwtXamQptAKUPB6wTIorvaGdTehk6bjQiQNZcY3+mm8dS9Jf7oCEafip4rFIp3JqpXvEKxjfz+Q7v54fHBpm2DpsHhZBRPwsF4hG/IJHCl5EhiY3Gx27aI6hrP54rk/YB51+Or2SKvFcrsizXn9KZ0jTP59UV4ZQwqsRObfDXthG1rkbkVB5iN0LUoyeRhbHsKIQRSVqhUrlMsvrkup3zFbjEaHccwEhRL5ygWz3Z1HdNIrBPnup6gWp3pab6muVrUPdf/R8xN/THnhn6Ohff9R0Sie1HtXM7hL1TwF0NrQ6Ov+T2vNxraJvT0HcoTvxNoKnquUCje2fTui6ZQKNqiCcH/vneMp5cLvFWssD8WYc7xOJqMcTIdJ6HrPDWQ5N9euc2fzWXJGBrLa1wz+g2d3bEIbxQrFNe0ef+ZuQtEyiX+ZHw/6KuC6nAyyrPLRZ6yYNeVc0wVlrCsMPXlpnycTPoBdD1HPg/IWiMiAASGUSQa+8z6FyMahXi7x43jN2MB2LnYcbkhQp5KHUPKgCBw0DULTY8RiQwjpYvnFXDdRRxngVLpAobR1+NcBEIYSLnqiBOLTpEvdN+2IZk8TD7/6urcjWfqjxfMv8B6eIT0mfcT5HoX1/5iBXOsoc7A0HC7bDbUDVrUaOGLs91sj01k/PgIRr+KnisUincuSqArFNtMRNP4+MFJvv3Fc2Q9n7zn40pJNZAYIkAADyaiPLtUwJMmvnTJ14T48VSMVwplvp5bnyz9sF+h+PorFIH3XbnEBw8e5t8PTiMiEd4shrnIf+VAcddB9r35da5cvlw/dqOkluHhIQ4cbLGjjXaWbbuXbsJZZINOqGtJpx6h6szV89PbYyCEjefmyWQeQ0oP3y/juks4zlyTAG+kWDpHOv1oU5qOpnUfVRbCwnEW2u6XwmHR+iuShSe7PmcjQckjKK3OXUtsb7Ho9kjnTmyD+4yKnisUincBSqArFHeAR1JxfmxyiE9dm+PxdBwnkOgCTE3gS3izUMHUBGdLVSYiJildYyIaaenUMhJ4fLOTY+ry2Xob+iAIKL7+Mn/HPktkz36W7Bh6EJDOL6M51W1RW7KtmNqcyBItJlV15ohGp+s52xser+lUq7e7uJKH48xgWUMsLz+3bm8mc4Ll5RdaHAfZ7ItkMidZXn6eqD1NtsvOogCp1JENc/ABonK6uV3sVtA2/yabY3HcuTI0FK/6xdZ1EPcFGuHr1QSxY8Mqeq5QKN7xKIGuUNwhfnbXKH82n+Vr2SLfaZl1WetLye/cmGe+1lxorJTjmJPn085w0/EPBVX++q2L5M6fRUpZF+eNVCsVqq+9XDcWXClnTE1PtxjdmnaZKboeJZV8qD4olTpa26M1RKFl7X+SzawKQpeY0NM8EhnC94oIzUBKH9ddolS6WB+7vPwCycRh8oVX25+wAcNItfQ197wS6fSj+H4Rx1msNx4SwkJKh+Xl5+nvex9Ly1+l28VIPL6fbPYUAJY1TCw63ZSas0LU3d3V+bohyDtosdpHuKj9nwBzLEFQ9fBmS8hyc9KKMRJDixk4V/MgwRyNI2ydIO/g5++CQO9xbadnImH30YCwgQASazxxJ2amUCgU9xVKoCsUd4iYrvHrB6f4W6fP81y2wGjEYNAyeTydYN710GXAj+duErx8Cj8IeOSD382pqk9EBvz40jUqr5ymN/+QzXH79jI7Rn+YVOq3kHIC39sPSFzXJbruwG4AACAASURBVJ9/ed14XY/j++sj/en0I5u6/kqTJMOIkc2dqm/XtAix2B5Ms49s9usABNIlnT5JtXqz5nnePhwdBK0FZ6Gw1unVJBabwjBSSOmjaRblyg1isT0Ui291nL+mxWsdUWXtuhUKxXNkMo/huosUixfq88ybL5PUntyeKLqkKeWlvtn1ca/kQQMtvvIRL5BugHe7OXXKnVl9H0XUCC0eAXeujCy3TgXaEr2s4SwN2aqraQ+dThUKheLtihLoCsUd5IlMgu/Z0cd/urXES/kyU1EfCRzxq3zbudMs3w57ewng+NkznJo+zI/kblJ55fSmr6nrvdvvySA0dKpU3svXXwhzm9///m7SSe4cQVClVLpAPH6gvq1UuoBtj1GpXCeVOoYmLMqVK9j2FEFQoVK5gesuAlCpXCUW290UhW+FEALfL1IqXWjabpmDGEYGz2t172KVZOJA08LC83IYRppK5TqRyCi6niAe34MmTKrZRbRBnWD2zpdjEkBQ7F5ky7IXRtZr6MNRgpyzvW4xPUTQ9XQEf269M5E7V6Z6JYfQBcZgFM1Wf8YUCsU7D/XJplDcYX5wbJAvzGX5awNp/uZImj/9ytM8+bWnWfZWxdPU1BRCuvygl8O+fJ72Tdc7o2kat26tbeq7MefOQTT6k1SrLrAiira5nXyH6OlKvahtT1KpXK9f3zASDWM8gsDDNPubLBFXc9M1hLBIp45Rqd6iUum8yEinjrZMR3HceZKJB8gXsmz0vdCNBMnEgzW3l3Cc52XxvCy2PYbv58jlwgXXwWf/PUHhDovzbXrbZNnfdivHbjFGovhZp+W+4tdmKH4ttL4c+P5DRA8PthynUCgUb2eUQFco7jBjtskzJw9w4fXX+YPP/QFLc6t50X19fSSTSXzfRwhB9Jn/viVxDmFE2DAMqtXum82UyxXK5W67Ut4Zv4/GIlIhTCKRYUwzg67ZJJMP4XlZqtU5qtWb2PYEYRrO0pqzBEjpkMufIZk40rEpk6bFKW1QoJovvF4vGm2H75fJF17DsoaIRXeRy79MEFSIxfbW0lsa2OY1TyP6UJSg4OBc3Z5OncaAjZNvLZK3GxELu9vKooc1ncK5nu/Y1Ck88M7PTaFQKO4FSqArFHeYEcvkz772HM//+Z+t2xePxykUCiwuLjI5uXXruKmpKW7dukWxuD5HvFckAtBWhbNY8U9vFE6rVn9Sipot4co4DSG02qFazX+9PZoewbbHse1RKpVrVCrXa5H0ZgwjhaZZRCLDlEoarrve2jAIqjju7IbXS6WOUqncqBeJtmN5+XlSqWPrmhitUKncAMBx5nCcOWKxvehaBF2PUyqdXx0oBWLQR279rWmJHjdbpoRsFuluf6630AXmRKL2IyJqBcoCP+/gL1UwJxM4V3pYYGzKe1+hUCjuf5RAVyjuMJoQ/PXHH+P2m29w5UpztPb69VCAjo6Ocu1aJ3/vjUkmk1y9unHEuBdy2RFi8WBVjtdTUHYTBBUMI91URCqEJAhWovY6rGl7E4/tWc2eaYGUPpXKTYTYOIfe83J4Xq42l0nCSHqYd26a/fXH1ep8y+MjkTEsa4Bc7syG12kkl3uJTOaxlraNdmQH1erN+vMmUd6IkLyx/4c45P8uwfU7GErfJrz57RP7aGBNJHFnii0LW1dwr231/pFCoVC8M9Du9QQUincDQgieeuqptvtXun5uhXg83nnQNlCp3KBcvrI+ct0hQt7eV715VLnc/SKjUrmGrsdIJB4kGt2JbY+TSj2MpsVqFo7NZDIncN0F8vlXur7GCsvLz5FOP4omGt8rQdXpvphWYFGaeB1tTEPEei/mbXveqIF0ti9fXB+OIqvbdz5rOoVzNb+hON8UW/CCVygUivsZFUFXKO4SO3fuZM+ePVy4cGHdPt/fuhjyfZ9MJgNAtVqlXN7GCGgL1nYUFdrGgnMl3cW2JzD0BLqRZMVvsFqdxXU3dktpR5gG05wKE48fQNdjaMLE8wsUCmdJp460bVDULdnsi8TjB3CcOVx3kUzmeE/nlKLKrYH/j91v/HNESnLhPR8l7T1B/8I3I17rq3l994YxHCUo+7g3ty93Ro9b+Bvd7ugBEdNxb9yZyHj1/DL2gT6ESnVRKBTvMJRAVyjuIk899VSTQJ+ammJhYYGZmZktn3uuofh0enp6XTrNdmAY6eYmRY00Cfb1gqlcvoKup4hERtZ13EynT5DPd9eAqBvW+pebZh+utz3Fk8XiW5hmH31937Bh8WgrNC2O0GHm0U9je1O42jzz1p8wP/onpEZOMHbxR5EXzc4nqmFNp/CzVYJyC8/3lbdgE9k0srJ9kW5zJI5zaXu+92spPH2DoOjS9937EIa6IaxQKN45qE80heIuMjExwf79++vPb9++jeM42xJBvxvEY3taNikCOgpgx5lH1yO0+tiR0sO2x4hExrZjmuswzb51PudbwferlEoXkbK37pumkcKyBmCgyi3795v25bQXeHPvj7D4jZ9FG+ruo9m5kgs7bXotVLhkc6JVgDtXAkOAvrXItN4XafJWvxOUTs8y91uvEpTuQidUhUKhuEuoCLpCcZd56qmnOHv2LBCmogwNDTVFv7eDlVv+K7ntjtO7XZ5tC5LJI/V87Wh0F57fKLaaRaEmOn+cSNnaGUQTJroeQ9fjTQWXicSDlErnG4pPN4emRbd0/FqSiYNNzYm6perMIAmIRafbjpmzP8vc0T9hqvBPiL1yDFnsbfFmDLr4yxcAgXTyBNkZVt8r2fTPOoRAWFH0zC7QHLJ/8EnMyb3YDz2FMO32F9U0hG4iNAN0E4QOUiJLOYRXJChm8QuLBNl5/Nw80g9AaIRZT1rN0UWACB8jROgepGnhV+M2oYFhIAwLYZigm3izJjdegpFf+MdYU1M9fb8UCoXifkQJdIXiLjM6OsoDDzzA66+/DoBtbyB8tsBKmouu66TTaTKZDLlcDsuykFIyO7uxvWAkchvPyzY8H9owpUNojR8n6yOvQpgk4vtaRtqXs88TiYwSi+1u2h4EVTQtsiWBnogfpFB4bdPHtyKQm08BicWmWV5+HiGMhnShNWg+V1P/GuPxPnbN/yLaq8Pd+YIDQe4yuT/89U3PbwVzchJ8D/fym7iX39zy+e4G5dNPM/7JTxA/fvxeT0WhUCi2hEpxUSjuAd/0Td9Ud10plda7jWyVIAjqlou+75PNZrl+/TrZbJbbt28TBL15XCcTD5LNro0YrxWMHXzONZul5a9RKLzecn+1OoPnZYnFdtW3WWYfkciOnubaiGFkcGq2i9tJ2CBpcx+fy8vPE4vtIxrdVfONb4+nL3Fu5Ge5+dSvo+3r8j3bJgdHva9ve050F/GXl5n/jU+Q/dzn7/VUFAqFYksoga5Q3AOGh4d5//vfD8DCwgJjY9ufe73WZcX3/bowj8ViXZ3DdbNkMiepOrPto71dsuLishGOs0SlcotU6iix2G78oEqlMoPoIn2mFfH43o6NiDZDpXKNdPrhTR/vOPNUqzNd3xnIa2d4Y9c/oPrYXYxkv82cUaLHH8UYHqLy1lvc/OhHmf/Up9b9DigUCsXbBZXiolDcIx566CH+8i//klKptKkc8V6xLAvP8wiCoEvhIvG8bNu0lnWnaNggRIv9XcQDNE0nCMotmggJLGsIw0jWO4kiQeLj+yVcdxmnOotc0xxJyjtXfFssXkDXE/h+7xaC8fiuFnckOnM7+QfsHPtnBDc3iqZvjygV2tsrfiNdD292tZZj7t/+Bs6Vq4z+8i8htqHPgEKhUNxNlEBXKO4Rpmly/PhxvvzlLzM/P8/IyAi3b3ff9KZbRkZGiEQi3LhxA13XyWQy6PrWm+Ssja9q+sbpGt14VVer7aLdEseZw3HaF9Pa9iSVSnM3Vs9bxrKGNjyuW2x7kiBYcQoRCCAW38XS0rNkMicJggq53MsbnaKGhu9vzmO8rF2gPPU6kZsHN3V8R4RASybDx/rbS6DTIm0r+9nP4t68ycQnfgM9nb4Hk1IoFIrNoQS6QnEPOXHiBM888wy+72PbNplMBt/3kVI2fUGYsmKaJvF4HK0hurmy37Ksuvf50tIS09PTlMvlJtHv+z6Li4sUCgVGR0frx9+6datpXpOTk9y8mSSVHmVw8BRNUVkZdgXVNLu5i2aHwK2UELFGa8peq0XZJb5fxvPygIdlDVCtLiBlpafvI4RWipHIEI6zQLkcfh9KpUuk0ye2RaDrenTdAqDqzJLJnFh3lyGTOUGxeJ54fB+l0uV6mk0qdQzHmcPQE5uehzQ8rKkkCIE7X0JPWgghcGdq9pf65j/W9b4+jOFhnGvXKH/9xc4H3E+0cQgqPf88lz/yd5j89P+FNTl5lyelUCgUm0MJdIXiHpJMJjl8+DBnzpyhWq2yvLxxN81KpUI+39pXOplMIoRASkmlUiGbzbY9n+M49eZIqVSqvj2VSpHP57l2LRSiAwNpIpFXWp7Dskaanjc7m6yPlnveIhjpJmeY5vkf3lKzonw+jF7H4weAULAbRrpD6Wp3WNYIxeLZFnv8lp1EHWeZaDR0a0nED9YFerF4Ht8vYNu91BwI4vF9mGY/metPYn31AI5c/RnwiuH3Xe+PoCUs3As3enlpza9mcRF/cZHIoYNo8QTlr3990+e6G9gPHyOo/T44ly63HedcusTl7/leJn7zN4k9svnaAYVCobhbKIGuUNxjnnjiCc6cObMuir0ZVqLprut27dQSi8XIZDIAFAqFrgvr1qas+H5nNxpNa58LXC5f7+q6nVjJCY/H97K8/ALl8uUtnzMWncRxuk8/KpXOrT5pkdpTLG7cNMk0+4jFdiNlQLF4ob44iEUPYsmD+DuWQYA+k6kf4y9W8ReryHLrBVAnjNFR9NpizZtfwKq5DN2P2EePIgwd6bg457trQOUvLXH17/99xn71X5D60Ifu8AwVCoViayiBrlDcY3bs2MGuXbu4dOkSk5OT9ej1Vum28LTdwiCVSrBnz82W+wAWXMHvLE4ggbQZ4SdTUdKpRwiCKkKzWM15WRWo7SwWIcwXz2QeR0ofKV2q1VtUq70vWly3JlAlaFqMINiajaWmRSmWLm7pHGtxO1g/CmHiullKpfNN2+ftz7P47V+k4txgwPpmBj/3A62O3tSczPGxelqLdegg5ZfWFureQywLLRIhKJfB8/BmZvA6+Pi3QjoON376Z3CuXmPgx360q7oIhUKhuBcoga5Q3Ac8/vjjXLp0iWvXrjExMcH1671Hkx3HYXh4uN6AqFLpPY+7kX37ckTs/9J2fyA0LhRDoTkZTVPIdRfJ3BDp43s5CsW3SKePb0Kgm/UI+nL2BQwjQzJ5kGz2NJt1N9E0u6Og7nCGno9wnFlcd5FM+gTL2dUUGsddzaWX22V4XmdVrAZLS+BtzVZzO4kePUr5hRewjxxG2FGqb7yxpfPN/Zt/Q/XsW4x+7GNo9/GdAoVC8e5FCXSF4j5g3759DA0NsbCwgLdJYVStVjFNE9u2qVQqjI2NMTs7SxAEXae76LqOaZoAzM8nSTk/STrzn2p7m9vFBzIBLAErniYbYxjJen54KAYDBDrL2dUCy+XsCyQSD4bn30T30GTyEJoWIZc7jZQenrdMNnsK257AMFIbRvDbsVnHlRUMI04kMkK1ept4fC9BUAkrZmu+8AINEDV9HH4fw8iuIJAumhYnCIrrzrvsPYPxoST20m5A1vW1fmr92F7x5heI1rpxlk+fBv/O2VUCWHv3IqtVtKgdFrkK0fDtEHg3wrz6yiubr1FYS+4Lf0r13HkmPvEbWDt3btt5FQqFYjtQAl2huA/QNI2TJ0/y+c9/ftO56AMDA9yoCZkdO3Zw8+ZNDMNgeHi463OOj4/XO5BeubISgf/WlmPFoIDktdr8O5/bNPvJZtcXHZrmAK67UH8edumkbTFpe3QKhdeR0iManSIIPKrVMEXHcebxvCKJxIN4Xm6dG8tGhI4yGtBb99UVws6he9H1ArncS+v2rzi9SOm2OLo9QVBlNvhjSDZv3zHx2KY60AXFAuaunbiXLoPn1QtERTSKLG9tkbIhQqBnMvjz81TPnus8fhupnjvHpb/9PYz9q39J8qmn7uq1FQqFYiPeZka3CsU7l6NHjxKNRjd9fKP1olVrzOJ5Xv3xdtOYv6ttEEGPRqdIpY6ht7EWtKyhpucrjieVyi3S6RNkMieJRHaQTB4hmTyMoLWHezQ6Ue92GrF2YFmDJBIPkkweIRbbiectUSi8hm2P9vQ6V17DViiVzmOZg0Qi669tGMmexflGiB5OZR89CtEomCb+wiJ67B6ke6wUNt/YvPvMVgjyea7/+E8w94lPIru806RQKBR3GhVBVyjuEyzL4vjx43zlK1/Z1vNWq72ninRFgybfqNhO1+MtI8et0TDNAZA+jjtPtiH/2nWzBEGZROJBgqAMSEqlS/X9ljlQ9z9vTJsBsO0JACKRHSwvhx08TXOAeHw3rpvFNNKsppnI8HFDiremWVt2gylXrqBpURLxgxSKb27pXBvidBaZIhYD10XoOtSi497sLH6hRVfUDoWU1p49CMsECX42izk2hnfrFsaOERAaQaVM9dXXWh5rHzmCZtv4uSzS3b5FymaY/83fpPLqq4z92r+qu9koFArFvUIJdIXiPuLkyZM888wzXeeMN9Joj9j4eCWnfNtp0G1buRUnkMTjBzCMJMXihbZ2hqEoB8NIgUyQL7yCZQ1jWYM4zgJOLTWmFZVKWHQbiYxSrYaFlqaZbulh3opIZLyXl9SWICijG3c2Si0iFsbwEOhGKMB1HaFp9X+l76H39VN56y3Kp041HStL6x1vrIkJZBAgdB0tHkf6PngeUoCQIGwbP5fDuXQJPA+h6/iFAu6LYUQ88uCDRI8/Cgik41B5OfSrjxw6BIZB9cIF/MWtFOFuH4UvfYlLH/7bTHziE9gH9t/r6SgUincxSqArFPcRyWSSxx9/nHPnzjE311v3y1ZRbCHEpsR+dxdcfaiL9hLddXMbnqZQfKvHC/tkc6eIRncRsYZAaFSrM5TLnX3Kc7nTRCKjRCIjOE73onAl7WarRKPTZLPNHTo9r4Btj1OpbE+Khww8vNlOPzvd20ZWz7Zq0NSMsCN11xe35kCkDwxg7dqFNztL9bVaBF3X0Wue+/7SEnpfBmvnTsr3iUAHcK9e5fJHPsLor3yM9Ld9272ejkKheJeiBLpCcZ9x8OBBnn32Waanp7tuGgRhpHxF1C8sLDA5OUkQBDiOUz9Xo2Bv5beudVPtWWOtc0s6fbxpT93zRQZEIkMEgdtzgWYrQp/0AMe5hesuE4/vqReWdkO1OkO1OkMycZhujSh7eR/WkkmfoFK9VXvdknT6BBAgZUAud5pi8Sy6ngg95KVX74jaC/3eI0T/m4MMJLx2qfMB24ysrEmjMgz8hQXKCwvN230fv9bdNnr8OOWXXrqv7BxXkOUyN3/mo1ReeZXhj/4MwlB/KhUKxd1FfeooFPcZk5OTDA8Pc+XKlZ6OGxpaLbYslUqUaukKk5OTXL16dZ3IFEI0bRsZGekt2t4UQRctHVrWkk4f37JAD6V/gG1PYpl9+MHm/N6dnrzNNy/QXS+L6y6SSj1MLneacjl0yUmljqFpUYKgjO8XyOZOkcmc3NQ19KKJ/Nz2WRBumW5/ju5Dcd7I4u/+LpXXX2f81/81xuDgvZ6OQqF4F6FcXBSK+wwhBI8++mjPx60V4NPT00xPT1MqlTYU5wMDA/T397OwNtrZ6XoNovXB1MCGYzXNJhbdhZRb99P2vHDhUSi8jh9UEUInFtvT1t2lPdvd6Kc9vl8klztNPL4f254EIJd7iWh0cs3IzXW2lPr94z5ijI12JWaDFvnu9yOl55/n0nd9N6XTp+/1VBQKxbsIFUFXKO5DHnroIf7iL/4Ct0dni6mpVTvAlXSWVmkrqVSKRCKBruv4vl/3T++JBi05YlmwwVRNs59S+RJsg532ilMLgJQeUmqUSheIRnf25rQiuxe1uh7D9/M9zHIV3y8Sjx8CoFh8AyFM0ukTuO5CPZq+GWLGTjL/shz2PCpfQqRSEATYBw9Q/vqLnU9whzDHxuse6hsR5DauTbif8GZnufL3fpCRn/95+r7v727oWqRQKBTbgRLoCsV9SDQa5dixY7zwQncuIxBG0FeaDDUyObk2SgvZbJZcLrel3Grhr4qUaoeUBsvM1JsGbZUgKBOL7qJUvkQQVNG0SJguIsyeBLq8SxH0sPhzdQEkpdtkH7lZNGnBhZv1dVL91dxr8Sgl1s5pMAyc8xfaDgvulP3nncJ1uf0rv0L5pZcY/eVfQovF7vWMFArFOxiV4qJQ3Kc8/vjj93oKGyLdVYFbDdqLXduepFBsL9S6RdPi6HqSaHQKKzJEJn0STbPQhImUPqUeotGJ+EFisZ1dj5c9RNu3RmdxbehJNGGhy3YNqO6tQC+fOYNz/QbO+QuYO3ei9/W1HOdns0QOHcQcG0Pv77/Ls9w8uc99jsvf+71UL939YlyFQvHuQUXQFYr7lIGBAQ4ePMibb96ZpjZri0TXEovFGBgYaOn2AkBDfV8lCND0KOL/Z+/N4yM76zPf73vOqb1UpbW0l3p3t9W71N5xbEwINthmCw6LYwIOhsxcEsgwl7khYSY3GcjnkpuZOwkXCHdikmCCbQyDwRgDXqBt3Lj3du/qRfsulVSl2s8594+SSiqpqlQlldSS/X790aetqrO8VV1SP+d3nt/zU6wIxYYQFkxhBWFBWDwowokeKTZOMROPp5VYbADT1Kfzy1Nrd7tbCYWyD8LJhWbxEAj8ZvENp1EVB2VlO0gkJgAwzRix2HA6m30+FksVDkcz0UgPVlstQqT88eHwVcCcFvypJBe7vQFFsTA1daEAaa3ge2Sm8pwr/nD1vPVZmdP4mRgYyN0IGo8TO5v6bNv37AEhUgkv+vL7FFaa2MUOrr7/d6n/8pfw/PZvX+vlSCSSNyBSoEska5ibb755xQR6NgzDoKGhAdM0GRgYYGJiIue2ZnxWCJ4Mw3fHBCkjeqYZ3SZUbq/x807b8taWiI+nPdtz/ebfHHXw6pADq6LxoH8Hu/TChXehKKplQUqNqrpzbu90bkxvH0+M5D12JJKqxJZ7D4BYrNHVwMRcEHGZuck1FuiAVl+P4nIhbLbZDPQ8RE+cAMDS1JTOUV/rGFNT9P5vnyb68Mep+ZM/kVGMEomkpMjfKBLJGsbv9+Pz+RgaWnxQTjEZ5vOpqqrC5XIxMDBAPB5PP56vwj5XoOt50lluqGrkXsdlDAOuWm+iQgVv5NWi1jeubuBMvBosDamQxaRAV+oxEVyc7AIEcUPn12NDaJU3YMLsl2lO/5n6fr9SXLU9RbYhUCpCaHOeE9PNg3NT4AsnMPEaXu+NWZ9zaZtTnnMA0XHNi+T5UCsrsTQW1ihq37mT6JkzYBhYN23CLLIpei0w+s3/j8ip12n826/IKEaJRFIypECXSNYwQggOHDjAj3/840W3dTgcRR3bZrNRXV3N1NQUo6OjWWMW8wp0w0QVKrqpkzByC6sjY/2cD7oJJayEjRO0VTTwYO7ic1aG8fGNKycW3e7M5BBnJvNfzOzbtoFQaPHpmHNJJhcmjiSTqbsL5eU3pO0ypgll7p0LpoUWihDZ3+/yRwXmKzM+/kWMMNe4R9TS3FyQOAeIXb2KpakRkjqKy0X07NkVXt00QmBtaSF+9WpJDhc+dIgr730fjf/tv+Hcv68kx5RIJG9uZJOoRLLG2bVrF+Xl5TgcDnw+Hz6fj/LpcelzKTSRxefz0dTURDwep7u7m7E8Y9bzDS4SCOyqHYCkkXvgTNhIMBSbImwkAMEmp6egdc7FLKHojMT6SSYDRe2j6yFstoYFj5eV7SQen33/ystvwGTpDaVLTtWZY6/Ia39ZBRJFDNgyQyESXd0k+vpACNQsn+tSYt24AeeBdqybN1Pq2xDJoSE6H3qIyInFLyQlEolkMWQFXSJZ49jtdpqbmzl16hSRSKopsbGxMcOKArnFtKIouFwu7HY7Tqczd9NnFgzDoKKigsnJSfQszXtW1cpUcoqYXnhkXjGyKKg0MKlUIVD47YZ9/Kxv+cNijCWpfQWrtXJBVKSqOAkGZyd4JhIBTDOJ07mZSKQb04zPP1D+syRVPMr1gABzRmoLzED+qaeOXbuIX7mCpamJZJ4LrpXG0thIYimZ+kD05EmsW7YgLBaS/f1Zt9F8NViamogcLexzYNu2DcXjwYhG0IeGiV+5SvzKVZTKSiy1tUta5wzWTZtQKyowJieIXexIPZhI0PvZP2XDE4+jraNkGolEsvaQAl0iWQfs3r2bU6dOpb/v7e3FarWiKArRaGrUfTjHZMbO6Yrm1NQUFoulqPNGo1Gi0Sh1dXUMDAwAoJQrCKdA79OxqanOz6HwEC7NxVRyqujXlo+fRBp5ZSjlGb/ff0tJjimEKLp4arX6MoT47MEyv52amrXOOBz+ogcRaaMKjs92FLc4ANNEDwRSKSjXEK2ubskCHSDe0YHzQHsqYQgTxemCZBLF6URxOYl39xA5egz7rl1E5/w8ZMPR3p7TamOMjZFIJLBu3ozqKQMEif4+kgODi67R0tyM6vUSfX328yDcbuw7thM5dpxEby/dn3gE/6OPorpdRb1+iUQimUEKdIlkHbBp0yZcLhdTU7MCOB6P09LSkhbghbCcwUQzDG0a4nDwMO/gHdiU2WiWQptUnx/uotO1lbbySnap3YAgEZsVdb3aLuJYORg06Zicrfb3REsz2Oa52FZ89r2MxzMvaGbemRarSQMjmAKOJ3y8lVegSNuKqnqW+F4vzZ4SOX4cx/59BVeWV4wsefGOPXsQFkvq/TBNTMNIvUpVwZz+O00MDKBP90CEX5sV1Y4DB4hkGdYVPXUKx549Oe0kjv37F/XBG8Eg8WDmdFjbjh1gEo8MbwAAIABJREFUmsSyJCepFRVYN24kcuwYiXl3ocxQiMhrhxFlZWjVVVg3b8IIBaVAl0gkS0YKdIlkHaCqKrt27eLVVzPTT7q6uigrKyMYzD+Gvrq6Gk3TFthiCkWv0FE8CiYmUTPKvrJ9iE2CYGL2vEqBLS1j8Qhj8V5eG0+JcrfmZJNnD7/vOovA4G+vXsHIIvQm46UZDf/CwEn2+/ZzdKgQr3Af2zbuxiZs+Fg8SWcGXZ/EZiss0cMZaqDydAsiAZpwspTLEMuGDZixpf3dlpJEX6Y1xdHWRuTI4g2zjn17iWRrUs6T6hI5cQJHWxux8+cxQqH049atW4icPFnEqmeJTTepqpWVaDU1KC4XKAroOpGzZ4kcPZp3fzMYJBEM4tixA0td3ZLWIJFIJCAFukSybtizZ88CgW6aJpWVlYsKdKvVSl9fX95t8nHIPMSxxHR1dq6LYlpNakLDWGJzZCgZ5tRYBz+y7meLHQwzu7i6OnkVTWgkzdwNqSvB317poNJWwV/4sjyZt0i++AWLYlopC7ZgfCslYq179y5pjarXS/T0aTSfD2uLP6MKvVTUqiosTU2p0EjTAMPMsHUs2N7nIzltg5rBjEawXX89ZjxOvCO3dScxMopt+3bMaIT41dk7QmKRGwqRI0dw7N9H7MJFtJoa1KoqIqdP5x6OVCD62Bh6EV7+ZHk52rS9KPCW23DMuWCQSCSSpSAFukSyTqirq6O6upqRkczBN9maN+czNjZGZWVl3sSWpbKrehdD4SEGw4v7d3Phtrp5ceAkL+bZJmEkpivf+auYuahz1eHQHIjp/4ohV857IjmB07GJcOQyiuLCMGYsSFpBDaL+H+wn/rOlRTJmYBgoNhvJsTGsLS3LPx6phs/oHAuJ6st2hTKLtbGRyJy8fsf+/YtWnGdIdnenBtM6HDja2kAIYpcvETl9ZtF9Z2w98VAIrlwp6Hyl5viHPsiex5/gwvvey4gQnPd4+Og1WYlEInmjIAW6RLJOEEKwbdu2vALdarVSX1+f4X8WQqS/X6pAj5nZjRe7q3dzcmRpdoK5uC1ugvH8dwGAotJisp2jI7CEBkwgqsf4jXIrHiXB9uTspNKpqfPTw4rA7d6GolgIBH6DoliwWCpzNolquGn8X60Y52crzo729gyrRjEkh4exbtmCGY0SWymRmqUq7dizB9M0iJ48BWrmFNRETw9YrVCMrSoSKcgSs9ZoHhig5533oJomAxMTVKkqFy9exGq1YrFYcDgcVFRUXOtlSiSSdYQU6BLJOuK6667jlVdeSX9fN8/nWltbW1TTaKGEzOzCca4HfTk4tMKGLEWT0aKP7bV5CSfC2DV70fvOENNjPNZ5DK/Vw3/2ZVovTDOJx7OPWGyAWKwfq9WH07EBM890VVBJ/DSzoVOfnCR+obgBSumjVZQTu3wZx44dxC5dwtHeTnJwcEEz43KYuchTq6uxNjdjJOJEzpyBaZ94cnAQtbwc66ZNGLEYsfPnl201WcsE7riDqbpaGv/tu9Q+9X1+9alPMhlLXUCGw2G+/e1vZ2z/4IMPsnnz5muxVIlEsg6RAl0iWUc0NTVRWVlJWVkZ4+Pj6ejDGZbjM8+Hipr18WA8yPbK7ZwbW5h6UQwzcY35qLBVcGni0qLbzbDRs5FAPMB4dByn5uTSeOH75mIiPknQ0ownmSl8JydnxXY8PoRhxHHYG7Meo2pwJ2WH3MRJ2T80nw9LUyOxy0uvfCd6erHW1RE9exbF7U4nmKi+GoSqpaIlAdMwwDBSYlvXU38aRvpxYbEgrBaMYGiB39wYH0eprESfmiJybGFajLDb0bu7C7a1rGcMm43fbN2CRVVJPvgRxsrK6Jtzd2pmXsFcvve97/HII4/g9XpXc6kSiWSdIgW6RLLO2LZt24Jm0Rk8Hg/j4+MlP6fI0a03Ehmh0Z1diBaDRVk8n93n9DEeK/y1mZiMR1Pbh5PZM+KXQp9Zj4dMgR4VHjQzikbKzpFMBgiGFmaSu0INuC5VEH/2UPoxIxZDqCq2LVtSaSFZxO9iGMEgsWAQtboafY4FSh8aLuo4iwVDGnksUvGLF4s613omsn0749ON2UMAWd4Xp9OZMZsgHA7z5JNP8tGPfhRVzX7BK5FIJDMUlosmkUjWBAMDAzQ1NeWswjmdzhU5b6ERiktFUxavFdjV4iwqSSNZ1D4uzUWZtQyrYs27XUdsobj6P7oNzqpti57D98/VJP/1UMZjxsQE4dcOEzl8GLOAht98iAKz6K8pcy/2hEA4nQhHYRantULPgQOLbuPI8pq6u7v52c9+thJLkkgkbzBkBV0iWUfYbDYcDgctLS2czJL1rGkr8yOtiFnh1+ZrYyw2hoKCEIKksXyf8dnRs1TYZpvozCy1XFUprurYE+rBbXFDDs1bZi0DSKe6BBNBjKRBW20bRwZzNyoeHDqPUnsLhplapYmJYZ7kl+MBLthvxMCcfs5Mb+Mz3HziFwqJK8dzHjedub0MLI2NJIcKz2tfbRx795IY6EetqCR++TJmLIYZDmPdsiVvDONqoVss9L///VT/+tfYr17Nud2Wxx5j8KHfpz/P3SqrNfuF3quvvorf7+f6669f7nIlEskbGCnQJZJ1hNvtBmDLli2cP3+eWCwz1cQwlpZFvhjCnK16mphcmZj1S2+r2Lbs40f0CBF9oW93LrmiDpeKgsJEfKLo/aJ6lOf6FgrtixOdXMxxuN3u64j94iKOPbuJHD4CWaaMaj4f0eO5BXwhJOb1JKwl5sYuJgcyIznjHR2pPPMrVzFWwKJVCLrHw+kPfYizgXH899zNTV/9f3OGcZoWC/FF7nbku1j+wQ9+gM/no7q6sGFWEonkzcc6uB8qkUhmsNvtVFZW0trayo033rjg+ampqSx7LZ9cTaIwW4leSRQUekO9Re+XrRI/Qy5f/YoRjxN57TCOffsyHlbKyrDv2kV8GfGIituNVluLuYZTU8x4/ohMPTCBES0+padUnP5wSpwDdI2N0fPhD+XctuOBDzA6mX+yrZLnbkg8Hufxxx9f8mRfiUTyxkdW0CWSdcbMP/z19fULngsEAiiKUvJK+lyLy3wSRu5x7KVgT80eTo2cYiQysvjG8zCzVKpXkrbaNganBimzluGyuDg+dDw1+XTOtUDk5Em0+nq0ygqEw0nk9dfRI2G02lqSg0sb9mTfsb0k00NXCkdb26L55kYwiKO1lURXF8mhIaybNmHqOorNhhGPo03niBtTUyTHx9GHi2uAzcfwu97F2XmV+7g1e7KQ7vFwtYCfr8U+e0NDQ/z4xz/m3e9+9+pfLEokkjWPFOgSyTolm8fVMAwqKipKnuRiFbkbJ0vhQc9Ftb2aqcQUhll6606x00QLYXBqkJ5QDwAeqyclzE3YmawDTqc2SiZJ9veT7O9HrayEaJRExyWs122DAgS6o70dU08ijOn7A6ZJ9NLyIyRXCq2hnujp04tulxweJjk8jKWpCaWiAmG3Ez9zBmGzYcZiJOZ4whWvF9u2bSguJ6ga+sQEyYEBjODCXH61shI9EIAcojre3MwrVZUwzy424ZhtMNZdLtSZu1ORCFVWK8WboxZy4sQJ/H4/bW2LNxhLJJI3F1KgSyTrlFxVcqfTuaoCPZ+NZLnEjNiSp39C9sp/vasen9OHKlTGhxa+T3E9zs6qnUDqtQlE+jWapgkCDNMgEAswNDWEQervob22ncODs1Vsj9VDY1kjG5MVvPvPX8q6Pn1OPJ/qdKE11COm15zonbX0aL4aLM1+YhcupDPO1wuW+gaSff0Fb5/o6UFxuYhfvgyAOU84Y7FgRCLE5g11sm7ahLp1C5HTZ1BstlRspaoQv5jyt0cOL6zgm8CRe99FNEtM4sWxMfZYLCiJBOc/8mF2fP0bCEBNJIgVcGem0LtYzzzzDA0NDVnviEkkkjcvUqBLJOuUXLfQVyLJxUqe6MES6nMVFX06dsWqWAnGSzOpdC41jhpODJ/I+fypkVNFH9NtcTMZz/Qk94R6IAR3D7dBYvG7DPPzzx3tbUQOH8G6eRPGVHhRi8haZSm2HSNHL4Vj3z5QVeKXL6N6vRm+/RlBrzU0YMZiGQOTcllIej78YbpyZLsrisLIve+i8uVXeH1ykk2bN2G/dJl4UyP9E4vXzwsV6Lqu8/jjj/PII49gty992q1EInljIQW6RLJOySXQV8J3vdI56DPs9u3m4thFQskQcSNOk7spbRkpFq/NyxbvFoQQdE524ra4CSVCnBxZGE+5XEKJELqRPdVDWBYfwpR9x9R7rnq8xC9dXurSrilqdTWJnuL//oTTiTlnyA+ahm3r1oyLGDMWWzCYCSCZZZpuorcPx/796MFg2goT3rObQ3muLg3D4EWrlZ3vfjfmRICX3vpWWu66iwvxeEHNrHOHFC3G+Pg4P/zhD/nd3/1d6UeXSCSAFOgSybolV4VucpF0iaWQz69dyguChJ5gZ/VOonqUyfgk/VOFWyPmU2YpoyPQwUR8Ap/Th02zcWVy6Ukpi+GxenBqTsLJMJrQsGt2DNNAE0ucGhmP4zhwYIGVYz1h9fuJjBTf3GtvvZ7k4BCazweGgRmPE3399YxtjKkp7Fu3LhDo2Uj09REbHGSqrQ2zphrn0DCOkVH22B0cnQrl3ff1idRE2EAwyMLZsLmZmJgoqmH7zJkzHD58mAMFDEGSSCRvfKRAl0jWKauZUDK3qrcSzZUz2DQbCSPB8eHl5YHPMJN4MxQeYii8sgN8jg0fw6bauK7iOgbDg3htXlyai8T40hpchdWCEYthqatD93hIdneXeMWrwBLThJJDQyS6ukh0deXcxr5zZ0G58Rc//vGFItzvT302IoVXuYvFNE3Ky8uL6gd59tlnaWpqkn50iUQic9AlkvXKjEBfqemhc8lncSllk+hyhhGpqFiEBZfmAiAQC9DkbirV0goipsc4P36eQCxA52Qn50fOUD25tF+zpgnxS5dIjoysT3EuBLElpsuo5RXY9+zJf3hrgdahHNeThmGs2GCvGYr92dR1nSeeeGLBADKJRPLmQwp0iWSdMiMuGhoaqK6upmI6J3olKLPMDiNaydSWYCzIVLL4YUv7fPvQ0UmYCaaSU+z37SeUCC2p4bNUvHdiK995vJ7d5/JPSJ2L4vXiaNuPo60NMxbDtm0bRqTw/dcS1i1bssYeFkLs8uW892ms27ahT5TeylVqVLV4e9PY2BhPP/30qmf4SySStYW0uEgk65R4PE5zczPBYDB9G91qta6IB30qMUWTu4kaZ03Jjz2XvlAfdq34JIu5WewbvRvpDl67irMwTb52eA8VP0+liJjVdQXvq1VVETkymz5i3bQpo1lSuN2oZWWpqaFTU+ihaeuGaYCZyvxWXK41EcWoer1L2s/S2Ijm8xHJZ18xTeIFVufdgQCswl2mbOSbJpqP119/nY0bN8p8dInkTYwU6BLJOqWnp4fuedaHlRodrpgKPaEeekI97K3ZuyLnAIjoEdxWN1X2KkajowXvZ5gG1Y5qvDYvVtWKU3Pic/oQCK5OXiWUyN8IWEr+5kIbFT//TWkOZtHAYsFSX4fmq0UfHyN+6TLJ/uzNs1pNDbHz59Hq63Nus1okujqXtl9vL4neXhx79+YU6UYRF6G2wARUVy1pLctlqQId4Cc/+QlNTU3U1taWcEUSiWS9IAW6RLJO6Z0zyGalsZuzVe35MXAxvbR+WYfmKHo6aSQZobmsmWNDx9CERtKc3b+ttg3d0EvWeJqPPxraxYanMsV57MIFLH4/mCbC6SB+PncqS3J0FEfb/ulseROEgn3nTsxIpKCqeHJwENXjIbGE7PFSYmttJVbA9NC8KJmfM8eBdhK9vQihZAxxWgytgEjElWI5kYnJZJInnniCP/zDP8Rms5VwVRKJZD2wqEAXQtiBXwK26e2fNE3zi0KI/xO4HzCAIeCjpmkuCKAVQnwGeJjUPzmngD8wTfPa/caUSN4AxGIxhoZKn0rS3NyMEAIhBNFpYSOE4JSY9XLPbxgdmBoo6RrKrGWMR0s3CfXI4JEVrfrP8Duhjdz5L6cXOPSNiQmM6cE2tp2teY9hTExkWly2bEHYbIgCLRrJ4eH0/9v37iXR1ZUxrXS1EEvwXs/HiEQQFgtmIoFSVpZqli1iIukMyjUU6MupoAOMjIzwzDPP8J73vKdEK5JIJOuFQn7rx4C3mqYZEkJYgINCiJ8A/5dpmn8OIIT4NPAXwCfn7iiEaAQ+DVxvmmZECPE48HvAoyV8DRLJm47u7m5aWlqA2WZRwzDS4to0TUzTRAhBMBhkooDJhwChUGhBLFxzczM25lTw5hQF65x1DIRzC/RtFdsos5RhYnJm9AxRfXGxZFftRae5VNgrSOgJ9vv2c2zoWNZttpZvxWPzcGLoREaFvRRsS1Tx8HdGMRexGBUbURnv6MB+/Q70QHF9Bc4bbyR86FBR+5QKtbqa6HKr54DicmPfu5f4pUuo5eXpSaFFH2edNtnOcOLECTZs2MC+ffuu9VIkEskqsqhAN1Ot5DMGTsv0l2ma5tx/MVzkHvitAQ4hRAJwAgvHvEkkkkXRdZ0LFy5w9OhROjo6Ck55cDqdeL3egkR6tlHjsVgMPLPfG+ZsNJ3H5skr0F0WF0eGjtBc1lyQOPdYPQyGBxkMF2fRODJ4hO2V23NOCe0OdhOIBdBNHZfmIpksrUD/1AU/9qYEkZFUtdqxf3/GqPkZoqdPpxsWhaKAoqB6vSTzWFKiZ85ib23Na+vQfD70SCSVO24YhI8eRdjtqazG6a+Mz8v0Y7brriN29uwSX3V2rBs3Lmk40XySQ0Op16OpSxbnAL033gBFTPVcizzzzDM0Njbi8/mu9VIkEskqUdB9UyGEChwBtgD/YJrmoenH/xr4fWACuHP+fqZp9gohvgJ0ARHgOdM0n8txjk8AnwDw+/3FvxKJ5A3M2NgY//Iv/1LU0JMZwuFwwSI9m21maGgItXrWsjC3Ctw12YXX6iWcCFPpqMSu2rFpNiyKBU3RMsT8Pt8+dEMnaSSJ6TGiepRIMoK/zJ/2h28t34qJSU+o+PHw8WQ8Z3Pp3MdWIiaydkojenbOxUEu77FpwvTFwcwqktEoaBqOPXuIHDmSdTe1ugpHezuC1FTMxJxx9o72diKnTsG87GwzkVh03YmeHuw7W4n39WGMpT5bttZWkgMD6KOFN+mmEYL4xYvF75dtbXmGFBWDJxAAq7UkxyqWUkUlJhKJtB/deo1ei0QiWV0KMsiZpqmbprkXaAJuEELsnH78z0zTbAa+Dfz7+fsJISpI+dQ3Ag2ASwjxkRzn+IZpmu2mabbX1KxslJtEsp4wTZPnn39+SeJ8hnA4jGEYlJWV5d3OYll8+Mu5sXNU2Coot5Vj1+xs9m7GZXUxGB6kM9jJhfELnB49zYnhE5wYPgGkKtjHho5xcuQkZ8bOcGniEr2hXsaiYxwfPs5+334AJuOTRJNL8wxfnryMYRpsKd+y4LkKWwXbK7ezt2YvsWRpm1qrkw4cnUOYyxkuk0zmHKgDoI+MEjl8mPDhw6jzfz8KsUCcF4qlro7o66cxxsZRvF6sW7YQO30a68aNWLduXXiuOag1Ndi2b0ebM/XStv069EBgSWtZKXxPfZ/bE0ns16DRMlHARVKhDA8P8+Mf/1jmo0skbxKK6mAxTTMAvAi8Y95TjwHvy7LL24ArpmkOm6aZAJ4CblnCOiWSNy1CCDweT95tKisr8fv91NTUUFtbS11dHRs2bMDlcqW/DMNAVVUqKyvznivr43PUYzgZZjw2TiAWIBALcHT4KD7n8m69nxw+SWtVK31TfVwYz51yshjjsXGuTFxhX82+BY+fGzvHeHQcnaVPK83GZ7t3keiYl8ldRHqHVluLdetWIoezV8+BVOV95tDFLjAPM2JPlJVhqa0l3tEBQOTwYeIXL2LdsCH3vtEoemAci8+HpaEB4XKhOBwlXF1pEED9977H77z8ChsqK3HOs3F53W5cTueKnDsUKm2854kTJ3jttddKekyJRLI2KSTFpQZImKYZEEI4SInuvxFCbDVNc+Ze5n3AuSy7dwE3CSGcpCwudwHXfoKGRLKOSCaTBPNMZPR4PIyNjTE2J61DURScTidTUwunctrtdioqKrJW5HONPp+f3FJqkmaSs2Nn2VG5g9Ojy2sw1E2dY8PH2F2zm9dHXs+w2fSEeqh31dM/VZqM8OaEh9arOkutnTv27cVMpi4Y7Lt3ASIt7gXTNhghMu0eAhS3GyMUSqWbzEluKZZEby+2bVsxE0liFxZeGMUvXsS6eTPx7m5UrxdrSwvJgQGUsjL08XE0Xw2REyfS20eOZm/QXQvYOzq4saODyPbtvHjrLQTDYQ7YbPgf+w7hnTt5ZtPGkp8zGAyiKErOn6ul8Oyzz1JXVyetoBLJG5xCPOj1wLemfegK8Lhpmj8SQnxPCHEdqZjFTqYTXIQQDcA3TdO8xzTNQ0KIJ4GjQBI4BnxjJV6IRPJGI5FI8Oqrr3Lo0KG8lTiPx7NgemhjY+OCIUYzRKNRhBCUl5cTmGNHsFgs1NbW0pXF+7uYQL84fhFVqEWnr8zFMI1l7T+fk8MnaXQ3oonppsxp4RuKl66q+bkzG2Fy4cVTwVVuVSV6rLh89sjxE9hbW9EnJkgODqJYrdi2b0efnCg6htCMRIhdyO0Z1wMBrFs24ygvJ3LkCHp5OVpdHZgmsbNnSQ6UNmJzNXCcO8dbIxEiGzdS/uKLhNrbean1elihtBdVVUsq0A3D4PHHH+eRRx5Z1LImkUjWL4WkuJwEFuQ7maaZzdLCdBb6PXO+/yLwxWWsUSJ509HX18cTTzxRkO9cnZc57fF4GB4eRtM0dF3P6lmNRCIIITIaR3VdR1VVampqmJycTKW3TGOQX2CYmFQ7qotOX5nPubFztNW2cWQwj92jCHpDKzfMqVXx0nL2Knoo8+Kl8vaNeFtDXFnBe4XGdGOpsFpTlW9NSyWerABzrTczDaBKHpvUSiOsVix+P4rTCUIQnVPBh1TTrD4xgREM5ryAsHV2YuvsZOSeu3ne68VcwSjGUorzGUKhEE888QQPPfTQgp9/iUTyxmBl71tLJJKimZiY4LHHHiu4KTQyT1woikIsFkNVVaqrqwHSwnsu4XAYXdfT/vampiauXLnC8PAwhmHQ3Nxc1LrLbeVFbZ+LI4NHaK3KP9BnLfAlytl460XMaGYFvWpnGFvoENd9Mn/fwHIwEwmEEBixGFpNDY69e1dMoGcly7ksfj+WpqYVP7V9927iHR3Ee3oQmoY6/RkHUFwuomfOEL94EUt93aLHOtfSsqJNl1arFV0vbc/DDF1dXTz3XNZQNIlE8gagsPF0Eolk1Xj22WezWloqKytxTjezzQwhAujvz7Q1lJWV4fV66ezsxOFwUF9fj2EYjI6O0tTUxNDQEPHpgTqhUIiysjIqKioyGkQTiUTGFMTX4qnGNAWFHZU7cFlc/GYwc6S9UytNo51Tc5I0SptTXmputvnYcP4VhKmjOizowdnkGV13o6pWlMA5Gn7vrczcfBAWUC3mrP9FQLDXYKm12/iVKwBYWlqInj+/9BezFOaJTuFyYcZimLqOxe8vWURiNmY+psbYGJGxMRACe2srwmYjcvZs2qoSOXYcx759xDo6MOb0cMRaWkhUV4Nh0LuMZKRCqKury2oZKxWHDh2isbGR3bt3r9g5JBLJtUEKdIlkDZFMJuns7Mz6nM1mo6dn8XzwcDiczkrWNI3u7u50lbCnp4eKigrsdnvatz7TgDq/Yt/b24umaSSTSd7uejvPJp5lLDrG6bHTtPnaUlNCrbMe2NHIEnKz51Fhq8Br83J+fJUFZ5H855gNMe2XV+yZv0Yvf/0SjR/ah4fn8fL87H1KffprDpPBm5Z0fqHMcbkbBmaeJuKVYH7V2b5jB5HD056eigoc7e2Y0SjJiQmSOXohloLi8WDOd/ibZs7JpZFjx7C0tKD5fMQvXSJRW8sLv/221DKtVpjTWL0S5EpFKiU//OEP8fl81NUtfsdAIpGsH6RAl0jWCLqu88QTTxBewtRDVVVpampiYmICXdfTVfVwOIyqqhmTM8fHx3E4HNTW1jKYZ4Kl3+9P22fCA2HGXGMZiSjLiUNs8bRwa8OtPHbusfRjda46MOHq5FUALIoFh+bg1sZbOdh7kGB8dUVoLuyo1PXPCsLGe8rp/qFBfHAS19Ya6t7qxDL2QkHHmjyxxCZLcW3diYrdjj7nLk+iZ1aE6+PjabFu27Edbffu1AWFooIQxC5exIjHcezciRGcRHG5MWIxYjlE9lxsW7cSKTJmMNHZiaO9DYBYczMT0+tefK7u8hkZGUEIsaI2mmQyyXe/+10+8YlP4FiDMZcSiWRpSIEukawR4vF4zuQVyD+VsKmpKV15b2pqSqezDAwMsHnzZi5dyszpjkQixONxmpubc55zamoqLeC79nVhBGbF+XLSVg7UHcBf5s8Q5y2eFiZiEwRiqXXfWH8j92++n4O9B/np1Z+uSiWyUKLoPL/5Rt52+qcAWAMvs/l2piu7fYixwsWYY+9ejGgSoSiYukEqWHH6tc7kLAoBipLKQp/zGXDUVGPGExgr2OCYDdu2bZhCoDU0YAQCKC4XsbNns24bO5stfTdFWsRv3YricuHYswdTVUA3QEwn72sqczNxCpmOOh9LYyP62Dij738/I40NeCIRvF5v3p+1UjE1NUVDQwN9cya/rgTj4+M89dRTfPCDH8ywpkkkkvWLFOgSyRrB4XDwmc98hl/+8pf86le/KmrfGZ9rQ0MDuq5TXl6Ox+MhkUgwMjKSdR9d1+nu7kbTNBoaGhZ4ZeeK4lE9075yZeIKAoFJcZVBTWhsq9jGt89+O/3YdRXX0R3sxqJaeOj6h3j/tvczGZ/kUz//FDfU3cAHrvsAh/oPcXniclHnWkm+EL3EnZ5jVl6OAAAgAElEQVQG1MlZ4SWKfC8AEt29xLuWnjTj2LOHaA5xvFLogQAWv5/YpUsYJfBwxy7Oxjw6b72V8MsvL/uYc1HKyoidO8eVG29gLB7HarUyODiI3W4nGl3a1NpiKGQ6bym4ePEiv/zlL7njjjtW5XwSiWRlkZfaEskawmKx4Ha7C95eCEFLSwt1dXU0NTXR19dHf38/Xq+XaDSK1WpNxyjmoqGhAUVRqKyspKysLO1lnanYK06Fy8FMcTwRn6DKUZXxWLWjmhZPS95z/bt9/y4jh3xX9S7eu/W9fOGmL/DUfU/RWt1KIBZgc/lm/vKWvySqR/np1Z+uKXEOMGXE+XnzrmUfR59aXvXbiC91RNIyUAT6+Di2PFNGl0yJrSCirAxzOi40KQTj4+OMjIxQW1u7KuIcWDCjYCV58cUXuXLlyopaaiQSyeogK+gSyRpjMUE9w8xgoRlry9zJgjOPzUQo5qK2tpaRkZEM33s4HKa6ujrtWzcajdSYsXk4tEy/62hklM+2fZY6Vx1PXHiCn1z5CQAf2/kx/u3cv7Gjagd/0PoHfPqFT3ND3Q3cs/EeekO9TCWmePbqs3zh5S9gmAY1jhq++rav8icv/klB78O14jFC/M7svM8lYWQZclQMsbPnsF13HWAiNI3o6TPLOt6iaBoIhfg8y1SpSHR3Y9u+nfjly1g2bCCeZbppodj37MGYnEin3cylp6cHh8OBz+fL2ZRdKsbHx7MOE1spvvWtb1FRUcGePXvYv3//or8DJBLJ2kQKdIlkjbFv3z6GhoYYGRnB5XKlBw4F5yV1NDQ0ZIiL+VUzIQRTU1N5zzUyMkJNTU2GQNd1PcMWY6omLuFiKpF5LK/NS3dw1sdrYnJk8AhfvPmL/PnLf55+PKbH2F65nS/d9iVUReVz7Z/jJ1d+wjdPfZOe0MJUmuHIMN85+x28Ni9OzYlNtaEIJV1Fv7HuRg4NHMrYZ2fVTrZVbqPB1YBds3Nu7BynR09zdeJq0TacQjkZ6ccsq0MEi5veWWpi0xGLisu1oufR6upA10n2r+DrNU1i51K+dXUZwlK43SQHB2cHFWkagTk/H6ZpEolE6OzsxOl0EovFViyvHKCiomJVK+nj4+O8+OKLvPTSS9TX17Np0yY2btxIc3NzOuFJIpGsbaRAl0jWGDU1NTzwwAN8+ctfTjd7ZmO+oEjMa6ATQlBVVcXQ0FDeYwQCAfx+P4ODgxnTQ9PHOSe4Y/cdhNwhhvVhzkymqrQ21bZg2/HoOBfGL9Ab6mV3zW5ODp/k6sRV/uq2vyKSjPAfX/qP/KzzZyTNJG2+tqwCHSCUCPHere8lrscRCKocVfz3o/+dm+pv4nMHPsffH/t7LgUuUW4v50PbP8Q9G+/J2kgaioc4OXKS40PHeW3gNY4PHSdpliZjPWkmSVjsLEfuCJt1SY2P2ViOrUG43ZjJJEJVEVZrqklzujlVCEFychLV601fDKwUinM2S99chgXFtmkT0ZMn098P33svEznen3A4vGii0XIp9K5YqTFNk76+Pvr6+jh48GA67WlGsDc0NKBpUgZIJGsR+ZMpkaxBLBYLO3fu5MS8MeZz6enpoaamBqfTyeTk5AIRYBgGExMT+P3+BTaWuUSjUXp7e3G73VkFOoAz4MRus+NwOjhDSqBnE4QtnhZe6nkJh+Zgv28/J4dPclP9TbzY/SJfO/E1JuOpKqIiFCJ6BKtiJW7E0/uX28oJxAI81/kc3/ztb3Ju/ByT8Un2+fYBcKj/EF957St89W1fRVMW//Xltrq5peEWbmm4BYBgPMjzXc/zUs9LvNT9Usa5i+Udrg1og0u3lJiGwAjlv8NR1PHCYRSXC1PXwTTTfzr27SVy+EjuHW02zFAIzedDWK0ksmTtO/btw1jkbkwpULze9P8Lu33pB5pz8ao2NfG8NX+jps1mw+VyoarqilS6A4EANTU1DA8Pl/zYxaDrOp2dnXR2dvLCCy+gaRp+v5+Wlhb2799PWVnZ4geRSCSrghToEska5frrr88r0IFF/8GPxWJ0dXWhaVpeH6yiKHmrfAfLDtIf7oc5u89ELW7wbGBn9U721+znvi33cWQoJQbrXHW8c9M7ub7qeh5+7uG01WSTdxNj0THOjM6KW6fmpMHdwA11N6ApGj/o+AE31N9AW10b49FxoslUNdXE5Nf9v+YzL3yG/3DgPyzalDqfMmsZ922+j/u33M9EbIIfXf4RT154ko5AR+HHUB38g20Le888hzCWUf2ek2Vu2+THsaEcUwcjbhD89etLOmQ2EZ0cHMLS0EAiV9SfkYrPTOa504IiZkd4riDmnIvI2LT/XK2pQR8fh2QSrFaI57+osu/eRez8rHc9fN11i669q6sLVVWx2Wx4vd6CKt757jplw+kszaTdUpJMJrl8+TKXL1/G5/OxY8eOa70kiUQyjRToEskaZdu2bWzZsoWOjsLFYy6SySRerzenQE8kEnkrfHXWupRAn8OViSscqD1Aa1UrL/e9zOXAZX7R/Qva69p5+t1PM5WY4i2Nb+Hjz308wwc+MDWAbqTEvc/pY3vldj7a+lEq7ZU4NSdem5fbGm9DCIEmNI4OHeWvXv2rjHO/2PMiB3sPcvfGu/n91t9ne+X2gt+LGSuM1+blwzs+zIe2f4hTI6f4uyN/x+HBw+ntfA4fCBgKzwrXD3pb+VzfVSxDPy74fIvhattB49ZDqKTSbUxTJb6xhXB0IwNPLR6hKOw2FJc7ZUtRFPTJyQx7SKK7G8fevZiqmnrtQoAiSPT2obhcaL4a4ufzN2NGjhzF3nr98l5oAZhzBmppdXUkkkm0Wh+K1YqwWkkGAhh5BLpSWUH88pV0cgtAT3V1QefWdT092Mvv92OaZtY7UzOEw2EqKiowDANN01BVldHR0Zx3qvLZ1dYChV5oSCSS1UEKdIlkjSKEKOkt51weZbvdjtPpZCzP2PMpY2FldjI+yWuDr9ER6CChJ2j2NNMb6oUBeHjXwxwfOs7nf/V5BqYyp2Xu9e1lg2cDbbVt3NZ4GzbVRiQZwWVxpcXzzQ03A/DkhSf5L7/+LwBU2iuxq3buaL6Dq5NXeaXvFZ6+/DSHBw/zo/f8CKu6NDe4EILdNbv55tu/yddPfp2vnfgaDe4Gvnff9zgxfIJHfvYI1ZYyvmHbypYTTyOWMaQp87w6vve2Uan9KCNDXQgdm3EZ1RYkcXcboz85mecoYG/dSeTIrIXF0d6eHgKUxqKhj45mVKgtGzeiVVUt3DYHK54QQ+YdgPiFC9haWwHQGhoAM2siy1ysjU1ET53KeOz83OFPBaDresZMgLq6OlRVpa+vL+NnyDRNBgYyP9vV1dU5BfrExETB1flrQWjOZFiJRHLtkQJdIlnD+Hy+khzH7XZnbYKzWq2Ul5cvEBoAwi5ApP4ciWUfdgQwHksNqzk7dpb7Nt/HQ60P8drAazz83MMYppGxba2zlv9623/lzOgZ6l31OC2p2/5ua/bs93Nj53BoDj534HM0uZt47Nxj/Kcb/xPPXX2OV/peAeD9296/ZHE+F1VR+aO9f8TO6p18/pef56Xul/DavDzg2szn+7vQRn+w7HPMp3LjAKI3+4WTZg7j9I4zmvXZwrH4/eijYxniPMXaysq2tLSQ6M0c2pTs7QVVRR8dRVgsKGVlGMGF0ZSOtjaMaHQ2tWUaZc9ugsu05sz8bHg8HkKhEMa0JSjbBe/IyAj19fVYrVZM02RiYiJDkHs8njUr0OOLWIckEsnqIgcVSSRrmJaW4jzWubBarXg8nrTg93g8qKpKVVVVVnEOcHzbcZ6se5Inyp9gLJa7uj6XH176IW7Nzd8d+bsF4hzgtsbb0E2dmxtu5sTwQn99XI8zHh3n550/5+jgUbaWb2V39W4a3Y04NAdOLSXo9/r28qW3fInf2fA7HB4orAJcKLc33c637v4W/3LmX7AbOn/WewVtdGVyvxebPipIIhwOFLcbYctMzVFcLmxbt6aH+1i3bMF+/Y4FQlxxuxFZplkqTlcxheUVRy1zp3zmc9ADAfTR1CWKmUhg3bQR5o2yt+3YQeToUWKnT5OcY9FSvF5euL50tpzJyUmam5sX/Zns7++ns7OTrq6uBXfAEokEzc3N+P1+amtrqaurWzMpKisZMymRSIpnbfxmkEgkWWloaKClpWXZw1Rm7CsWiwW/3084HMYwjJw56cIjCCSK98zurt5NZ7CTUyOnFjx3S8MtfLb9s3isqXzrcls5f/rin7K5fDOtVa2U28t56uJTDIeHuaP5Dg7UHWB/7X7u9N/Jp37+Kb759m/yN7f/DZDyrr9r07sIJ8J85fBXSOgJLGrpRqpvrdjK19/+dcoiQcRkjubKVcDFEbbfn/r/4dA7GPnRrN1FOBzoExMIR2pglBEMEs9ylyR2Jrs1RbHbr3kRXWuox1JXD4ZBfI6tJDci3dQKpJpfe3oWTiDVNE7d/Q4GSjhRUwiBYRhpG5bNtjBmdD6BQAAhRLranu1iuK6ujsHBwWs+/TOZLE38qEQiKQ1SoEska5y77rqLZDJJMBjk+9//fvpxRVFwOBy8733vo6Wlhf7+fn7xi19wJY9PN5FIZPhrc5KESLL4MfRv3/B2zo2dw6baiOmzTWcWxcJ7t743Lc4B7mq5K+0nPzN6hksTl/jYzo8tSGbxOX388f4/5mDvQd656Z2MRkaxKBasqpVD/YeIJCOcGjnF/tr9Ra83Hx6rB4YuQOt74fKLEMp+p2F5LE2UVb9rN1Z3nJHjgJ7E0daWkftdCEYyQbKzEFG8cgiLlcjRowVvHztzBsXrxYjFsPr9GBMTWS0vg/fdy9JycHLT3Nyc8bMTLSCnPRQKUVNTg9VqpXeefWeGgYGB9EW41Wqlvr4+PX20J0vk5UohK+gSydpCCnSJZI3j9/vT/x+JRDh48CCapvHAAw9QV1eXrug1NTXxwAMP8OSTT+J2u0kkEiiKQn9/f8Zk0EIwwgbl1nKmksVlX9/ScAvfPvttkkaSd295N7/o/AV2zc7/uOt/0FrVumB7VVHZXL6ZzeWb8x739qbbCUQDfOaFz/B89/MLnn9t4LWSC3QAmtpTX4YOp56AI49C169hzwchOgnnS5fmshhWewTbxmZMw8RqjyDQUR1ejGgUxWJBq6nJHaWYBWEuM2u8BKjl5SSKuDtkJhLYN23C1PWcFySxu+7ixVWYllmoZ3smGcnv9+e8OO7t7aWlpYWhoaH03bLJycmS3D0rFFlBl0jWFlKgSyTriJtuuom2tjYgZVeZj91u5yMf+QjxeBxFUdA0DV3Xefrppzl+/HjB51HLVaJ68ZMcfzPwG9rr2jk1copP7vkkwXiQ8eh4VnFeLFbVyh7fHqocVQxMDbCrZhfv2vQu+kJ9RcUsLglFhT2/l/o69A2o35MS7ie+AxefgzP/a4kHLtwE7tVewnvj7PemqTEWv4XYxauoFRVYG/NknWfBjMWwNDYuaKxcTYQy/foVJWVTKcDmkRwZIdHdnfU584Yb+GF1VSmXiN/vJx6PZ1zk2my2nPawXHR1deHxeLDZbAviTJPJZFYh3tvbu2rJL1KgSyRrCynQJZJ1RjZhPh/rnAqiqqrcd999mKa56OCjGUzdLGhS53yevPAk//Pt/5OnLz3Nb/p/w1d+6yt88uefLPo42XBanHxs58cAeKHrBT79wqf56vGvAinv+7ff+e2SnGdRbvxE6s9YEKq2QFkdBLqhr3CrRhqx9D59IZL4d/2GHvutTB05SyRHhr2luRmtro60ncZICWFhs6FPTODYv5/omdOY0VlLkqO9PT2NM3Lq1ILmzVIROTZ90WgYOA4cIPLaa4vuk02cC7udjvvv4zCUfKBSLBZbkICUSCQyvOWFMjk5ic1mw+l05oxjnEsymcTlcq2KQJcWF4lkbSEFukTyJkBRFG655RZOnjyZU1SYmonSkhKMHZ4OBgMLGw4XYyQywkB4gFsbbmU4Moxu6vzFTX+xrLVn407/nRx/8Di6qZM0klkTY1YcWxloNgj2w+i8YVKqDRr2pQS4ABCp6rAQMDeXO1j8ezwXhSg12/qp2LIBIXR6fxxIe7Id7W1gmBjRyKLCV62sRFRWgmFiJhIZ2eiKy4WxGtXVZfwddt53H4dXaNJptgFDhmHkHeyVj1gsltfuMh9VVfF6vcTjcSKR4vtCCkVW0CWStYUU6BLJm4Ta2lruvPNODh48mNU/m9yR5IehH6a+WeLQw0AswM+7fs7u6t385at/ycO7Hsbv8S++4xJQFRUVtSQZ6EumYV/qy10LP/0zmOiGqRGo3wvdr67KEiwMIFQDw3TMWkaYrk4XWBXVswypsvj9aD5fwYOMlotZQNNlNtS6On69gnGRuSZsOp3OJR+zkAbTGbqn7xjU19evqECXFXSJZG0hBbpE8ibi9ttv5y1veQtjY2O88sorHDt2LDV4xQIvJ15e1rF9Dh9JM8mr/a/ysZ0fIxgPcnrkNLtqdpVo9WuYlltgy11w6QXwNEHPoVU79ejYjYz99AQwmfnEMgWXMTVVkCe8FGi1tcQu558SmouxA+0lt7XMYLFYSCQSWZ9bzuTNoaEhbDZbTvF/LZAVdIlkbSEFukTyJkMIQVVVFffeey933HEHx44d4+DkQUZHlz6zUlM0vnDTF/jbI39LjaOGq5NXuWfjPfRN9b05BDrAnX8Gzip49vOretryynO4fq8JhIkwDUDQ94s4yeHiknvmo4+OYtbVlWaR+VBVFLebZJYM91zMpM+Yra08t4xK9nIYHR1d1Es+M9RI1/UFkYkej6coi8xK56TLSaISydpCCnSJ5E1MWVkZt99+OzfrN7P54ma+dvJrjESKF3ZJI0nCSPDXt/01P+j4AVPxKb548xfTEZBvCoSAmz4F0Ql48UurdlqbeQUbVzIi1f13X8flf17ecR3t7USOHFneQQo5z549RWWhA3Tdey/9Fo0+w6CU3Qf19fWYppkeKJRv0i5AZWVlToFut9uZnJxkfHwcSDVu2+12KioqiMfjGY3chbDSAn0tVfMlEgksPUJAIpG8YbCoFh7Y/gDPvPcZ/mT/n7CtYlvRxxiJjFBmKWMiNsEN9Te8ucT5XH7rf4fW91zTJVjF8qMTjXB4xS0uzvb2osV54o47eEVVuGIYlFJSlpWVYZomuq7T2NiIx+PJK84Xo7q6Oi3OISXQJycn6ezspL+/P2vzaT5W2oIiK+gSydpCVtAlEkkah+bg47s+zge3f5AHfvQAVyevFrTfF278Ag9sf4DzY+cZjSzdKvOGQAh499cgEYELz67qqbtf30+4YwRDN4Gle9AtTU3Ezp0r3cJyYJomwmLBzOHzzsblutqSr8Nut6PretGCPF9j5XyP+vzvp6amUFW1oOZMi8WCpq3sP9e5vPYSieTaICvoEolkAU6Lk3+951/52ft/xnPve44/3v/HNLob824PcF3ldfzTO/5ptZa5drHY4Xe/Bbs+sKqnNeIGRjQJieU1iKoVFWCsfHRl5MgRLC0tCJut4H1GVuDOTG1tbUG55PPJZ1MpKyvLu28ymaSmpibvNvX19Xi9XhKJxIIs9lKTSCSkSJdI1hCygi6RSLLitXnx2rwAPLzrYT6282P8uu/XPHHhCZ7veh5zjun5sbOPsbN6Jxu9G1GWMXznDYXFDvf9P6ks9JP/tiqnLMVbb9uxg+ipU8s/UIGo5V7iHR2LbziNJkTJrTcDAwNUVlYyNidu0ul0Eo/H81pL8sUeKsrifxmL+dCtViv9/f2LHqcUmKbJP/7jP1JTU0NNTQ3V1dVUV1dTVVVV0HA0iURSWqRAl0gkBaEIhVsbb+XWxlv5i5f/gu93fB+AG+pu4Mtv+TK9oV7CiXC6mi4BLA54z9cAE05+d+XPpy5ToatqetDRamDbvn12mmiBuFbAFx+LxRBC4PP5GBoaAlIe8nA4zNTUVE4hPjQ0lDXJpbm5mc7OzkXP29PTg8vlYmpqKuvznZ2dRQ01Wi5DQ0Pp1z+DEILy8nKqq6szhHtNTQ0Oh2NV1iWRvBmRAl0ikRTNJ/d8EqfFya7qXbyt5W3YVBs1zvy369+0CAH3/T2EBuHyiyt6KkVdnv3DuW8f4RUcTJR4651YfnUQEgnUhgZ+s38f+0Mh9HkRhPnY/cxPCNxzN70lFurRaJR4PE5LSwuGYaRFscvlorGxkd7e3qz7VVdXZwhoh8ORHi60GIZh4Ha7cwp0gK6uLpqamujv778mw4RM02R8fJzx8XEuXryY8ZzVasXtduNyuXC73Rn/v2nTJiorK1d9vRLJGwWx0tFNS6G9vd08vErT6yQSiWRViE7CP90Ng6+v2Cl6zh8geCy7kFwMxeWk5h1bwNARwiQesjD23ImSrS1+1118v6aaHUKw75e/4pXfup2rhkGZELzz9BnMkyczd8hlZWlv57ubN63YcKJcNDQ0EAwGCc67wzBTYR4fH0fTNLxeb1EzBVpaWgqqtjudTioqKnJeKKw1XC4XDz30ED6f71ovpWCEEEdM02y/1uuQSEA2iUokEsnqYPfAB78D077+lUAoSxetlXduodLyLJW2n1Fh/TllVaVrSlSu28YzNdUAnDVN/u22W7k63YQaNE0e37GdxJ13ZOwzcv/9XP3ABxBzBhGpfj9Pb9m86uIcoK+vj3A4jN/vz3jcNE0URUHTNBobG4se+NXV1UVLSwsejyfvduFweN2Ic0il1Dz66KMr3twqkbxRkQJdIpFIVotyP7zr/16xw4slWlzUinIq3b/KPBYRLI11WJvqsfobcbRuwftbuym/M/VV8bY9uNp2LHpspbKCn7W3Z2SWG/MEtiEET/l8jN1/PwjB1N138wu7jUOKIHDXXan1uN388rZbKT5rpXTouk5XVxe1tbUZgnp0dBSHw8HExETRx5yxkExNTVFVVbXo9isdt1hKwuEwjz766LLy5CWSNyvS4iKRSCSrzfc/BSceK/lh+6/eRODV4hsKfffvpMrxXNH7RZWthMMbU04UQcY0UxBMnA1xdN8BXi+i4r1VCC4aRrpKbgHuHRjkVH09F82Vj34sFFVVaWxspLu7Oz3l0+VyYbfbi66izzSC2mw2Kisr8ya3OByOvOkxaxGHw8GDDz5IQ0PDtV5KXqTFRbKWkAJdIpFIVptEJOVH7ztW0sP2d99M4OXF/cxzUSsr2PL2SyhES7oWgIN1n+XnA2vv35hSUlVVha7r6cmgjY2peQFTU1NYrVasVivBYBCXy8Xk5CRlZWVompbRSKppGvX19XR3d6OqKg6HY8FgoxnKysoW+ODXA3a7nQcffDD9/qxFpECXrCWkxUUikUhWG4sDfu87UFZf0sOKArK351N1e+OKiPOEsPPS6PqxYyyV0dFRQqEQzc3NCCEIBoP09vYSi8UYGhqip6eHiYkJ+vv7CYfD9Pf3093djW3OcKZkMkl3dzd+vx9d1ykvL6e5uTnr+QrJV1+LRKNRHn30Uc6ePXutlyKRrAtkBV0ikUiuFX3H4dF3Qjx7tbRY9IrrMYWTlNdk9itlFjEBI/Xn9O99U3GijJ5EyXCIl46D/j/m2KSX0cD6q/guhU2bNnH58uWCtq2pqWF4eDj9vdfrxePxZFTWrVYr8Xg8Y7+Kiop0ZV4sYh3K9nxvb2/e4UurwVvf+lbe8pa3LLr+1UZW0CVriTd+eUMikUjWKg174QP/DI99AIzliyZ1/ExxOzTdACskzgFu7PkGF2o+T3GO7PXLyMhIwdvOnSI60/g5Pz/dbrcvEOjj4+PLWCFrYiro888/z9DQEPfff/+aWI9EshZZn/fKJBKJ5I3Clrvg/n+4NudOrGyz4a+a/z1dg4EVPcdaobm5mcnJyYK3n2tVaWhoWJAA43a7izreeuP111/nn/7pn/7/9u48vq3qzv//60iybMnyvu8hEJasLAECYWuAkIaQltLSUmg73Sht6Tqd7tPp8pvSKd8ZOt1mSkvboaULhdIp0NJCSwdCWUJYwhb2eE9sx7vjVTq/P2SbOJYsyZIsWX4/Hw8/sK/OPfdzL/H1R0fnfk5Gn6NIPJSgi4ik2rq3wdb/t7DHzM6D/c8krfte39HsaE6fqivJNvWQaDSMMXR3dwPBRD0QmH2dlsIqnG1tbfzwhz9cVPXdRRaKEnQRkXRwyvvh/K8t3PFKjyE4Jz3xxpx53JZ7ecjEMxPV1dXFVFnF7XZz8GCwontVVRUtLS3JCi3tDQwM8JOf/ISnn07eCrsii5HmoIuIpIuNHw3ORf/LV5J/LJc7cpt5+lPNx2hsWhpTWyC20XOfz0dRUREOh4Ph4eGQo8fGmJhrqS9mExMT3HLLLXR0dHDOOecs2ko1IomkBF1EJJ2c+UnwlcPvPwrWn7zjTIxFbjMPA556nmgNlm08qsDPW9z30uM5ghuaj2DcZl7iVVZWFtPDocPDw4yPjzM6GvrhXGMMtbW1sx4YTRS32834+HhS+o7XfffdR2dnJxdffPGMh2hFlqLMu1uKiCx2J1wBl/0KsrzJO0b3q/H3UX8a1KyHvNdWiNxbchZ+v5+i7ACX2dvI7nyKyqbf849l91Gck1lTXoqLi+np6SGWcsV+vz9scu71eiktLaW9vZ3q6mqWLVtGeXl5QkeU06204eGee+45fvzjH8f0qYRIJlKCLiKSjo7eDFfcCi5P4vsuqIXhOKdQOHOg+xVofRQG2vAvO4sxRy4vm+W4jOXKwh04+18bBc7peJzLyl+KM/D0kpOTk7Ca4iUlJTgcDjo7O5mYmKCtrY29e/fS0dGBw+GgqqoKjyf2fws1NTX4fD68Xi8+ny/tE3SAffv28cMf/jBpnyKILAZK0EVE0lXD6XDZL8CZ4I/782vj78M/ElzwqOQoAJx776Ox/k080dzPlbUv4Nm/a0bzicLl3Ni+Iv7jponS0lLa2tri7sfn802XaBwcDC5YNVUXfcrExATt7QU6CUAAACAASURBVO2ztkdjYmKCwcFBDh48iNPpXBQJOsDQ0BA//elPeeqpp1IdikhKKEEXEUlnR26Ct96U4JH0BK0gPdQBgdf6yrKjvLNhH+XNf5h5tOwCbgpcxMD44kgOI8nKykpYhZqcnByam5tnzAsPt3hPYWFhzP0fmpDn5+cvmgQdgtOBbr31Vh566KFUhyKy4PSQqIhIujt6M7z9V/CLt8LESPz9DbTH3wcEp7nk5E3/uKzx5pDN7iu5jFfbMmc8qLKyMq7pF0VFRfh8Pvr6+kI+YBpupLyjowNjTMg571VVVbjdbkZGgv8+nE4nDoeD/fv3T7dpaWnB5/PNO+5U2bVrF6eccoqqu8iSogRdRGQxWH4OXP4buO0q6I9jYRdPEfQ2JSYmGwB3bsRmi2fMNrLq6uq4kvOGhgaampro6ekJ2yZcIjo6OkpJScmMEow5OTkUFBTQ3h75TZe1NuwDquls+/btSs5lydG/eBGRxWBiDOpOhQ/+HY7ZOv9+ipcnKCADgTEYH47Y8mT/zgQdM7U8Hs+ciXUkNTU1NDY2Rqz6Mtdc85ycnOnv8/PzycvLmzFKHsl85rGn0oYNG6irq0t1GCILTgm6iMhi4HKDKxs8hcE56ef+C5j53MITMJ7tzg8m+uUroe2xiM09+3dhEjXvPYUKCwsZHo78hiScePadMjWSXF1dzcjICJ2dnTHtf2iCn+6KiorYtGlTqsMQSQkl6CIii43DEVzQ6B23gbc0+v2MAzr2BL+vPRlqT5nf8avWQPfL0PFsVM2tI2vRp+f19fVRTSMJp7q6mu7u7rjjaG1tJScnh7a2NsbGYl9sKhFvEhbK9u3btWCRLFlK0EVEFqvl58AH7gsm29EoORLGg6X8CEzMf6XSQGz7mcA45Z7Fm6K73W727dsXVx+xTC0JV8UFIBAIxDVNZbHMQT/55JM54ogjUh2GSMooQRcRWcwKauDdf4QzP0XE6Su+SqhcG5yaMtQJg9HPXZ7mLQuOnseozLN4VxGtrKyc12j1lPLyclpaWqJuH2mO+lS99MMZY2hoaJhz38LCQoqLi6mtTUAt/CQpKCjgvPPOS3UYIimlBF1EZLFzZsG5/wz/cAfk14RvNzEK+3YHp6Y43dAXfdL4Wh8jMH4w5t3Ozo09qU8Xh1ZNiVV9fT0dHR1R1013uVzzmtbhdruprKykpaWF+vr6sO0GBwfx+XwJWwE1GbZv3052dnaqwxBJKSXoIiKZYtkZ8MEHYOUbQ7/e8+pr33e/AjXrYz+Gfyy2ee+Typv/wOX1+0nYIkkLpLa2lqGhoXntO1VSMRYTExPzekNQUVFBe3s7fr+fpqYmvF7vrDYFBQXk5eXR1NQU95SdZDnhhBM48sgjUx2GSMopQRcRySSeInjLT+GSG4LfT28vCU5rOdTgPjDO2FYprVoDvY3zCm1F0y+4um4POc7Fk6QPDAzMa7+GhgYaG+d3nWIdQfd6vbNKLYZK0Pv6+tK6nnheXh4XXHBBqsMQSQvp+5sqIiLzYwyseTN8+BE44qzgtsIQc477WqD6eMivhvrTgg+blq8M32/DRmh5NK7QSpvv4tPun/HehmaOKpjnQ6oLpLa2lr6+vpj3q6+vn3dyDpCbG3nxpynGGAoKCmbNkQ83RSSdE/SLLrpoUZWBFEmmxbVigYiIRM9XDpffCvd8GfY9GbpN667gf6ce/DTOYPnFfU/BxCEl+apPhMYHEhKWY/gAdY23cAUwVrqK572n8LumfPwpGDPKzc3F6/Xi8XgwxjAxMcHQ0BDDw8PzTs5jndZyuFiS6HBvBsLNeff7/RQXFzMwMMD4+Pi8Y0y0tWvXcvTRR6c6DJG0oQRdRCSTudyw5evQsxfu/BS8dPfc7a0fWh6BwnpwZIGvAoYPQOdzSQnP3fUMa3iG5dVn8J/71jMWSMBCSofJdgQ4t/ogx9nneSSwmvvbg6PLpaWldHV1hZxjboyhoqIipikuJSUlNDc3xx1vpCouU+rq6sKO1Le3t+N0OvH7Z35K0dXVBQQ/HYilskwy5ebmsmXLllSHIZJWlKCLiCwFRcvgilugeSf86fPBJHwuvU2QUzCvkorzkdu2g4/UOPj+vhMY9idmJP3oQj/nFDRTtf9eTEsvAMV1RwHBBN3jCT/33lpLa2srJSUlUT20WVRUxODgYNTJ9Vyi6SM3NzfiCH9WVhZ+v5/c3NxZb0KcTicVFRXTPx88eHDe8+3jtW3btpBz5kWWMiXoIiJLSd3J8J4/wbO/g798JTiyHs5I7FM84pHXeh//5H2WPWVbuaWxmECkuu5z+EzFfXj274LemdvXdd/B3a63U1JVT2fnzIdmPR7PjLnbDocDr9fLwMDAnHXQfT4fo6OjCVsEKJopLoWFhbS2ts7ZZmpBI5/PNytBP3zkvaGhISUJ+qpVqzjuuOMW/Lgi6S59nxYREZHkcDhg9Zvgyv+bX6nFJHIc7GJl441cVf9SXP3k9L8acrtjqIP3Fz5AR0cH5eXlM14rKyujt7d3+qu7u5vm5uY564pPzV8/eDD22vDhGBP5jUk0dcxLSkrIysqaVeEllESM/MfK6/WydevWBT+uyGKgBF1EZKnyFMKlN0JB+AQ0Vcqb7mB5PFVebOiHJC3wp+wLGR0dnU6Ea2trKS8vp7+/P+Q+7e3tIVfoLCsrY2JiYtZIfLyiSfadTmfENoFAgKysrKiOGe1CSom0devWmCrWiCwlStBFRJayghq45EfB6i1pZkvh3vnvHCZBv7/hE+xpDU7d6erqoqamBqfTSUdHB729vSH3ycvLo7W1ldramaUqx8bG5pz6Mh/GGLq7uyO2s9aSl5c3Z5tAIBB1RZiFHkE/9thjWbVq1YIeU2QxUYIuIrLU1Z8Kp3041VHMUtZ4O29v6MTJPEZ3QyTo485cdh547WHEoaEhWltbI9Ysd7vdTExM0NLSMiNJLygoiD2uCMrLy6MazW5vb5/zwUqPx4PL5WJwcDCq4w4PD0c1tSYRcnJyuPDCCxfseCKLkR4SFRER2PTP8Pwf4cCLqY5kmsFydOPP+WJWLiNFR3MgZxn3D9TxfE8Uo/2HJ+ieIpxOL4VeNwODM6eQZGdnk5OTE7YqyqEJc0tLC3V1dfT29jI8PByyfTxiWUV0rjrmWVlZMS2W1N3dTXl5OQMDA0k5r0Nt2bIl4ui/yFIXcQTdGJNjjHnEGPOkMeYZY8xXJrd/zRiz2xjzhDHmz8aY6jD7FxpjbjHG7DHGPGeMOS3RJyEiInFyZsGWb0DlWnCk19iNGR/C0/E4tU23cVnPt/nHI55nQ/kYwRnlYRyeoOdX4xhsZU1O+4zNtbW1TExMUFBQQENDA/X19dTV1VFXVzfdpqWlhbKyMhoaGjDG0NzczNDQED6fb7pSSiK43W7a29sjN5w0V4Iebj79XDo6OnA4HJSWlsa8b7RWrFjBunXrkta/SKaIZorLKLDJWrsOOB7YYozZAFxrrV1rrT0euAP4Upj9/xO4y1p7LLAOSM5qFyIiMn/GwIrz4Kr74fPt8O674IxPQHmazRNu2Eiev5ct7p18ruxezq8ewOcK8TDp4Ql6VnA6yAvjVdObXC4X3d3d+P1+RkZG6O7upqmpCWMM/f395OfnT7ft7OyksbFxuqJLIBDg1VdfJT8/n8LCwoScWmVlZVTVWaaEmzcey0qkhxsaGqKnp2fGG5REyc7OZtu2bZraIhKFiG/9bfAOMDWJLWvyy1prD317nkuIoQxjTD5wFvAPk32NAYl9okZERBLL5YaG04Jf530ZBjuh6UHYuwOeuQ2GOlIX2+B+OPAS1JxE9ngvGzt/xEYg4KukpeQMbm2vpW/MQOCQpD2nEFp2EsBB70gwcXc4HJSVlU2PWBtjpmuFNzU1kZubS05OzqzDH14rvLu7G4fDQX19PT09PXHVEk9Uqca5VhiNht/vny4v2dTUlJCYAM4777ykzNsXyUQmmie3jTFOYBdwFPA9a+1nJrf/K/BOoA94nbW287D9jgeuB54lOHq+C/iYtXbWusrGmCuBKwHq6+tPiufmIiIiSXKwG168Gx67ERp3LOyxjROMAwKTUzvKjoHO52c0se48BsuOJ6/1/tc2lh0HncEPb8ecPh6o/QCvBqpoan5toR9jzIwRaZ/Px+DgYMiVRF0uV8iRbmMMdXV1tLW1xTQSfujxpr4vLi5maGgo7CJJFRUVdHR0hBxFr62tpaWlJabjh1NZWUlPT0/cizBVVlZy5ZVXxjW6n2zGmF3W2vRaGECWrKh+U6y1/smpLLXAKcaY1ZPbv2CtrQNuAq4OsasLOBH4L2vtCcAQ8Nkwx7jeWrveWru+rKxsHqciIiJJ5y2GdW+Fd98JV+2AdZct3Jx164fs16ad0L0X6jZA9YngKQbAjA3MTM4Bel5btMjtH+Scjp/Q3DwzgT080Z1Klr1eL/X19dMPb2ZnZ4etLW6tpampicrKyphPbWqaTHV19XQ/4ZLzyspKDhw4EHaKS0dHR8JGqvft2xf3FB5jDNu2bUvr5Fwk3cT022Kt7QX+Bmw57KVfAJeE2KUFaLHWPjz58y0EE3YREVnsKtfAxf8NH38KNv9/cMRZkJULzuzkHM9TBMOHjGb7R6H5IWh7DEbmeChyYgSKl0//uL/8TCzRz4NuamoiEAhQX1+Pw+GIWOUk2tKGUzweDw6Hg+LiYtra2qan2oRLjPv7++ccoR8bG5sxfz5e8dZIP/XUU2fVkBeRuUVTxaXMGFM4+b0HOA/YY4xZcUiz7cCew/e11u4Dmo0xx0xuOpfgdBcREckU+dVw+kfgzT+Bz7XAZ5vgxHcl/jhFR4R/zUaYUuItAcCfX8/vOpdFfcjm5maKioqYmJigqakpqhKEsS5eNNXn4QsUZWfPfqPjdrujmqs+MjISUwxziWbV0nAKCwvZtGlTwmIRWSqi+VyyCvifyXnoDuBma+0dxphbJxPvANAIXAUwWW7xR9barZP7fwS4yRjjBl4B3p3okxARkTSQ5QWHAxw5sP3bwekwO66Lv19XDlQdD11x1Gjva8E63dyW/Wb29cc2IuzxeOjp6Ym6/XxWFw21iumhU0KysrKorq5mZGSE/v7+Od8oFBUVzZo3H494RtAvuuiimGq7i0hQNFVcdgMnhNgeakoL1to2YOshPz8B6KELEZFM5z5sZctz/wVG+uDRH8fXb1FDcCrLvPdfBv1tmLJjeOP+7zFa/XlebJudEIfT1tZGeXk5HR3RVa+ZmJiY9dBpJKHqqTc2NlJbW4vH46GpqYnGxkYaGhrYv3//nH35fL6Y3lBEEs3KpqGccMIJHHnkkQmLQ2Qp0RMbIiKSHMbAhf8Bl94IeVWR24czHud0jYI6KDka9j2Fy46yIfBIzNM2Yq3dHWp6ylwGBwena6wfqqWlhQMHDjA6Oorb7Y4q8W5ra4vp2JHMJ0H3+Xxs3rw5oXGILCVK0EVEJHmMgZVvgKt3wknzmOFYtwF64yy7ay1kZUPNeqhZz5HZvRTl58bUhdvtDlu9JVz7WIyNjYVdGdTrDX4yUVlZGdUKoX6/n9zc2M5vLvNJ0Ldu3YrH40lYDCJLjRJ0ERFJvuy84Gj6Zb+GY7cFa5pH4/AVQedjpBdad0Hro8Gvg904YxwRb25upry8PKq2VVVVYZPtuYRL6qdG72OZMjOfefDhxPrA6cqVK1m5cmXCji+yFClBFxGRheFwwDFb4G03wYcehLpTw7c1juDo+b6n4z/uyGHzzY1hmS/2BDbapNvtdkdV7WWKy+Wirq4u7CqkU4l5tImyx+OZ1xuEcGIZQfd6vVx44YUJO7bIUqUEXUREFl7ZMfAPdwZH00OpPSX4YOhE5JKCEQ12zfzZOCijM3TbOXR0dFBXVxdX2cFDVVRUUF9fj8fjobm5OWxSPVXzvKurK+Trh5uaEpMosUxV2bZtW0Kn14gsVUrQRUQkNZxZ8KbrgwseHW4ivqXlp2Xng/+wkWfjoHBs7kooU9aWTPAPDW2UegKcXjnGW/23UuKd+0+n3++P2G9BQQEHDhyYXjEUZi5MNPUmwOFwTJdMjHZe+9RCR4kS7QOvq1ev1tQWkQRRgi4iIqnjzoW333zISp8GGk6H9scT0//kAkUzGMOIMy+q3Ru8B1nW+GuuHv5PNu/7Hr62B3iP5248zvDTPs7IeprlVaFXAQ0e3uB2u2etBtrc3ExVVRV1dXU4HA48Hg81NTXTI+ujo6M0NDREHMFP9Ah6NG8MfD4fW7dujdhORKKjBF1ERFIrvxq2XQclR0HdKdD498T0a5zgC/Fgp3Ew4CyKqotqM3taSU7H43yk/CHcjtAPbR7Vez9eZ/gHOuvr6+nsDD3Fpr29HYfDwfj4OMPDwzQ3N894vbGxkby8PEpKQrzxmBRLtZlE2bZtW8LfGIgsZUrQRUQk9ZafAx96GE65Eryl8fVlHNCwEawfmh8O+fpBE10y6bahp9p42x/mgzXPzNp+ZtUozoEWBsdDV4kpLCyksXHuspGRqrX09vYyODgYdq53rDXbIxkdnXu60erVqzn22GMTekyRpU4JuoiIpAenC9a8Gd5zV3wLGxXWQ+MDczZZ23s3Xk/OnG1qfAGKDuwKf5iuR/FlvZZMn1d9kE0HfoaZGGFwNPQUmEijzA6Hg3379s3ZBoJJc35+Pm63m5qaGvLy8qb7T+Qc9KysrDlXUPV4PGzZsiVhxxORICXoIiKSXkpXwIX/DnmVwVKLRUcESzKWHhPd/nnVERoYyvoeZ03Z3CPNG4r7cBwMX+3FDPfwj+YGLm/Yz4fqX+SMth9gxgawQN/Q7OozJSUlEVf5DAQCVFVF9+akvb2d8fFxWltb8Xq9OBwOCgoKwpZrnI/S0tI5R/QvuOACfD5fwo4nIkFK0EVEJP3UnQqjB4OlFgvqg1NVepuhal0UO0dY0GcyL39d+39RkBe+JGCRibxqpxkbYEXjLyhvumNG9/m5s0sTJmNlzankef/+/QQCAdrb2xPa/1wPpC5fvpx166L5/yEisVKCLiIi6SfLCx9+CC74OuTkwZHnQdnRgAPqTgu2cRzyMGT5quB/q0+EpocidB7M0HPGe3gXv8WTM3uqS6U3QE3bXfMO3+mYOTrvdrtpbW2NuF9+fv50WcV04HCEThOcTifbtm1L+Hx3EQlypToAERGRWdze4Nfyc+DUq6BnL/z+o9C4I/h67cmAgYlhGB8GV3ZwcaPWx4g4gn7IlI38wZfJK3IzfNgqnWsrHJj9Xhif30JJgcNCKCgoCFu55VBerzeqOegLJVwCfuqpp1JcXLzA0YgsHUrQRUQkfVVMjowXNgTnpvc2Ql8ztOxMSPcOO8rw2ASF+T6GR8cYH5/A7c7ilL3XQc78V8QcHJ5Z+STcSPSseKJsl0o5OTmcccYZqQ5DJKMpQRcRkfTndMGF/xEsnfjwD4Ij5jt/BJ174urWAXxw/Idkjx5gPKuAF6q3UTjaiiunMvhmIBbeMpgYxT82xMjICNOT3Ym+9GEqapjPxVpLXl7ejAdPN23apJrnIkmmBF1ERBYHhwNwwOlXB39e8xbY/3RwWssD34KDUczdLlkBrpkrY3pHO8CRhXO8m7UtN0LZsTDSG3t8Jcuh4zmcpSu4MGeQO1teW6002pHx/v7ID6YupKamJiD4BsPn81FRUcH69etTHJVI5lOCLiIii5OnEJadEfxafjbcsBkmRubex+2bvVJp5RqwAcjOh5H+YB8jfbHHY5wQGIeeVznZv4dl9RdyY/sKBsZN1CPoPT09lJaW0tU1ewXTVLLWMjw8zNatWxfFNByRxU6/ZSIisvhVrYMzPhG5XVaIxYmy82H/M9D0IHQ8A90vx378gtpgScjxYfAH55+XNd3JJ7Ju4oKqPmKpdZKu00fOPPNMPRgqskCUoIuISGbY+HEoXj53m7HB2dvmWallhsEucMz+UNpxsJPT2n/M2/hfKrwRqstMGhmJ8ClAChQUFLBx48ZUhyGyZChBFxGRzJCVA9u/A64Qo+RTDvbM3hZd3jw3GwAT/k+qr/V+rgr8lG21/WyoGAvbLi8vj5wQddlTrbCwEJdLs2JFFooSdBERyRzLzoB3/C58slxYO3ubKzv+4wbGwDP39A8z0sv6lhvYPPgbyjwBcnNzaWhowO12Y4yhoaGBgwcPTj+YmU4CgUCqQxBZUpSgi4hIZmk4DbZ8I/RrB3ug7pSZ2/Y/M3NV0vlyRzd33DHUwYe4kY1FXTQ2NuLxePD5fDQ2NuL3++OPIwmUoIssLCXoIiKSeU79ALzlp5B1WNLc9Tx0vQQVq6HqeChfCWMDULU2vuM5smB0IHK7SWa4h9Nb/puP1T6FHe6dUWc8HaXrGweRTKUEXUREMtOqi2HNm2dvH+4O1k9vfwKyJlcLNc74jhUYh6EuqFgT025FLffwsZzfsqp4Ir7jJ5nf79cousgCUoIuIiKZ64Jr4Iiz5mgw+YSoMwFTXKwfsn0x7+bsb+LNfddzcX0viXliNfE6Ozv56le/yte+9rVUhyKyJChBFxGRzJXtg01fmqPBZEI8lKCFgfzhK7TMxfhHWdf0Ez5T+QBHFaTvdBItUiSyMPSbJiIima3sGDj5/ZBbNvu1gIW86uDc9ESIcsXQcDz7dnJ5//c4vXJ+iX6yZWUl4JMGEYlICbqIiGS2nHx4/Tfhqh1QUDfzNesHT1HijjUe/yJDxvrxOccTEEziZWcnoCSliESkBF1ERDKfwwF5lXDxD2Zu3/ckjPZBZZxVXKbkFCSkm2LXcEL6SZTs7GzOP/98rSYqskCUoIuIyNKxbCOc9O6Z2wrqoXNPYvq3iXnIs3b8lYT0kyhut5uNGzeyfv36VIcisiQoQRcRkaXl9d8MJuVTmv4OtSfH32/pscER+QTIbX+Qj9U+RbpWdRGR5FKCLiIiS4vLDRf+Ozjdr22Ld+Q7txyGOmBsKL5+JhkboKjlHo4vS9+KLiKSPErQRURk6Tl6czBJn15p1AZXF52v0hXBBZAS7DTP3oT3OR9aSVRkYSlBFxGRpenEd8KZnwx+3/RgcEQ9rwpKVgRLMjpiKCk42p+UEMs77ifLpH4Fz4mJ9F7pVCTTKEEXEZGl66T3vPb96AAMtMOBF+FgNwTGof706PrJzk9KeGakl7Or4y/dGC8l6CILSwm6iIgsXd5iKFoW/D5wyEi1nZzS0foYVK17bXvlWqg/LZi4u3Nf2+5PXt3ydfbZqNotL/BzcX0vxTmJf7A0EAhgE1ShRkQic6U6ABERkZQxBi65Ae67Fnr2zn7dPwLtTwYrtBCAfbtfey0rF+pOhYH90NcMGJJRdeXe8XUR27y+dpBTOn6F6RvgxdKP0T0S34qmoZg4V0kVkegpQRcRkaWtdj2suhge+n74Nl0h6qSPD0Hzw8HvCxqCyX4SRpmXewZ4jOJZ2wuzLauKxjjDPkxO+9MY/2jCjz3F4dAH7iILSQm6iIjI2rfCEWfB83+AOz9FzCPhhTXQ15iU0I7zP8sXCw9gpqbdYLAOJ47RPhz7uma1Pz/7SSqrj+GeNu+s1+ZLo+ciC0sJuoiIiDGQXw0nvw+aH4Hdv45tf/84FNRCX0ts+9VtgI5nwFcJngIYH4VsX7C/gB+cLpyOLOiNfmXRgta/UddQBihBF1mslKDLonBv073s7d9Lla+KFYUrOLLwyIT02zPSQ1FOUUL6EpEMsfbS2BP0lp2ACT482vT36PY5tO3oQGzHi2AiwX/elaCLLCwl6LIonF13Njse2sF/7PoPAC5ZcQknVZzE8eXHU+Yp48WeF+k42EFtXi0DYwN0jXSxZdmW6f37RvvIzcrF5XDROtiKAwd3vnont7xwCz/d8lMqcytTdWoikm6OOAfyqmGgLcYdLcl4SHQ+JnAmtD8l6CILSwm6LAoO4+DchnO5+YWbAbj1xVu59cVbcTlcuB1uDk4cnNHeaZx8/4nv0zPSQ7m3nN6RXrJd2awpXcN9LfcxOD443fbS2y/lZ1t/RkN+w4Kek4ikKacLXv9vcPM7Yt83lkQ2kLzSjONWI+gii5key5ZF45iiYyjOmVnJYCIwMSs5B/BbP6/2vUrvaC8v9LxAx3AHzQPN/OHVP8xIzgF6Rnu4fvf1SY1dRBaZldth9Ztj388/AbnlkdtlJW5+eCjjNrF/3sfHxzlw4EBC+xSR8DSCLotGiaeE2y++nac7n+bfdv4br/RF/9BUJA+3P8zz3c9zTPExCetTRBa5DR+Ep2+JbZ/+NsgpgIkRKDkKPIVwsAdcbnBM/skNTEBf6+S89cR7oeEKdnblJaSvvLw8Nm7cyJo1a8jNzY28g4gkhEnHlcHWr19vH3300VSHIWns7sa7+eTfPpnwfs+pPYdTq07lipVXJLxvEVmEfrgJWnfF10fpscFEff9TMDaUmLjmcFfFh3lovzuuPhwOBxs2bODss88mOzs7QZGlN2PMLmvt+lTHIQKa4iKL1Nm1Z1Pjq0l4v39r+RsF2QVa0lpEgpa/LnIbhwtcOeFf79oDzQ8BDshL/gPpF/T/krfUdzPfB1br6+u56qqr2Lx585JJzkXSjaa4yKLkdrq55aJbuH739fzkmZ8ktO/P7/g89zTew7+f8++4HPoVEVnSVpwPxgHFR0DnHtj1Uxjpe+310qPhgw8GHywd7oUnboJ7r4GxEGUTnVngzgP2JTVkM9zNys7byXa8g9FA9A93ulwuzj77bE477TRcLt37RFJJU1xkUesf62frb7fSN9oXuXGMzqk7h8+d8jmqfdUJ71tEFqmxg9D4ALx0D/Q2wfbvQm7JzDa9TXDTpdD53MztVSdA++MLEuZQ1QaubT8t6vZHH300r3/96ykqWrrrQmiKi6QTJeiy6N303E1845FvJKXvPHceG6o28N7V72VV6aqkHENEMtD4CPztGnjgW8GfK9cGVxkd7k7ucR1ZYAPsrnsnv20qDNvM5XLR0NDA3n/0NgAAFP9JREFU8uXLWbZsGdXV1Uu+lKISdEknStBl0Rv1j3Ltzmv59fMxrvwXA4Ph3Ppz+fLpX6YguyBpxxGRDLP7ZvjT52GoE2rWw76nglVcrD85xzvp3bD1Wnr6+unp7aOvr4/e3l4OHDjAvn37WL16NcceeyxlZWU4nYldzGixU4Iu6USTzGTRy3Zmc/XxV7Onew9Pdj6ZlGNYLM8eeJad+3ZyXsN5STmGiGSgtZfCcdvh79+GHddB2THBGuh9zdDfmvjj1Z0CziyKiksoKi6J3F5E0pKquEhGKMwp5Jozr+GmrTdR4a1IyjHahtr4W/PfZlV42bV/Fx/+y4d5y+1voam/KSnHFpFFLCsHzv40vO8v4B8L1j9P1gPotackp18RWVBK0CVj1OXVsbZsLadWnZq0Y9zdePf0SqT9Y/3c+cqd7Onew30t97Gnew8/2P0DlWgUkdAqVsJ7/wwr3wj+0cT37ymGkiMT36+ILDhNcZGMsqd7D7e/fHvS+ncaJ4/tf4z6/HquefgaHmx/cMbrv3/59wRsAKdxctGRFyX1zYKILEI5BfCm6+GvX4XHboThnsT1XXsyLPEHPUUyhRJ0ySgF7gK2HLGFpzqfomWwJeH9D4wPcPVfr56zzR2v3AHA/778v6wtW8vPXv8zHEYfVonIJKcLzv8qlB0Hd3wCJoYT02/dyYnpR0RSTlmDZJQqXxXfPOub3LL9Fr51zrcS3r/bEdvy2bs7d3Ptzms5MHwg4bGIyCJ3/GXwvnvAm6CHOTX/XCRjKEGXjJSblcu5Defy8RM/zrHFx1LhreCSFZfwuzf8jm+c+Q1eV/c63rv6vfzT+n8iz50XsT+vy8uXTvvSvFYW/flzP+ftd76dpzqfms+piEgmq1wN7/gdeEvj68c4oOakxMQkIimnOuiy5L3hd2/glb5XcBkXxhistUzYienX15Su4T2r3zP9EGg8anw1fGfTd1hRtCLesEUkk3S/Aj+7GHr2zm//ijXwwR0JDWmpUR10SScaQZcl7xMnfYKfXPAT/u9t/8fOy3dywwU34HF5pl9/35r3EbABbnz2xriP1TrYyof/8mEe2/8YB4YP8Oe9f2ZgbABA1V9ElrLi5fCO24KVWOajVnmlSCbRQ6Ky5J1Td86Mn0+sOJEbNt/A9574HiP+ETbVb2JH6w7G/GMJOV77UDvvuutd0z+fUH4CK0tWcucrd3Ja9WlYa9m8bDOb6jbhdGilP5Elo3g5XPIj+PklQIxv2Os0/1wkk2gEXSSENWVrOKb4mOmk/IyaM/j4iR/H6/Im/FiPdzzOTc/dRO9oL3989Y/ctfcuPvm3T/L5HZ+nd6Q34ccTkTR21Lnwhu+CKye2/fSAqEhG0Rx0kTC6hrvoHenlqKKjpre1Dbbxh1f/gMFwT+M9PH3g6aTGkJeVx8aajSwvWM7W5VtpyG9I6vFEJE28fG9wJN36I7f1FMOnX1EN9DhpDrqkEyXoIvM0EZjgmoev4eYXbl6Q4x1ZcCTbj9rOWTVnzXjTICIZ6q7Pw0Pfi9xuxQVw+cLchzKZEnRJJ5riIjJPLoeLNx/95gU73st9L3Pdrut475/fyw+e/AGX3n4p7/tz8AFWEclA53wWCuoit6s5MfmxiMiCUoIuEocVRSs4rvi4BT1m90g3333iuzzX/RwPtz/M/zzzPwt6fBFZIDn5cMWt4Cmau13l2oWJR0QWjBJ0kTi4HC7OrD0zpTF867FvcX/L/QD0jPTQM9KT0nhEJIHKjoG3/2buh0Yr1yxcPCKyIFRmUSQO1lpe6HkhpTEEbICr/3o1viwf/WP9AFyy4hK+fPqXUxqXiCRI3cmw9Vr4/Udmv5ZTCAW1Cx+TiCRVxBF0Y0yOMeYRY8yTxphnjDFfmdz+NWPMbmPME8aYPxtjqufow2mMedwYc0cigxdJNWMMnzjpE6kOg4ANTCfnALe+eCu3v3x7CiMSkYQ64R2w5i2zt9ecpOotIhkomikuo8Ama+064HhgizFmA3CttXattfZ44A7gS3P08THgubijFUlD9zbdm+oQZjEYji0+NtVhiEiiGBMcRc8tn7m94bTUxCMiSRUxQbdBg5M/Zk1+WWtt/yHNcgmz7Jkxpha4EPhRnLGKpCWnSb/VPi2WvzT9JdVhiEgieYpgyzUztzVsTE0sIpJUUT0kOjlF5QmgA7jbWvvw5PZ/NcY0A5cTfgT9W8CngTlrwRljrjTGPGqMebSzszPqExBJtStWXkFhdmGqw5ihILuAzcs2pzoMEUm01ZfAUecFv3e6oVolFkUyUVQJurXWPzmVpRY4xRizenL7F6y1dcBNwNWH72eM2QZ0WGt3RXGM6621662168vKymI6CZFUcjlcfHHDF1MdxgwnlZ/E8oLlqQ5DRBLNGDj3X4LfVx0PWXNUdxGRRSumMovW2l7gb8CWw176BXBJiF02AtuNMXuBXwGbjDE/jz1MkfS2unR1qkOYYWh8KNUhiEiyVK2FkhVQtCzVkYhIkkRTxaXMGFM4+b0HOA/YY4xZcUiz7cCew/e11n7OWltrrV0GvA34q7X2ioRELpJGnMaJw6TPsgK7u3bTPNCc6jBEJFmO26b65yIZLJqMogq41xizG9hJcA76HcA3jDFPT27fTLBSC8aYamPMH5IWsUgaqsytZFPdplSHMW14Ypgv7PjC9AJGIpJhjtseHEkXkYxkrA1ZfCWl1q9fbx999NFUhyESk+b+ZnZ37eaz93821aFMy3fn8+ttv6Y2TwuZiGScQAAc6fPJ3WJnjNllrV2f6jhEIMY56CISXl1+HZuXbabcUx658QLpH+vnyruvnLGIkYhkCCXnIhlLv90iCbB/aD9X3XMV5//mfDqGO1IdzgzNA818/4nvpzoMERERiZISdJEECNgAO9t3cmDkQKpDCelXe37FCz0vpDoMERERiYISdJEEmLATlHnTt36/3/q5btd1jAfGUx2KiIiIRKAEXSROd716F9tv207rYGuqQ5nTjtYdnHvzufSO9KY6FBEREZmDEnSROJ3bcC4rilZEbpgGekZ7+NLfv8TA2ECqQxEREZEwlKCLxMllXJR4SlIdRtTubb6Xj937MU13ERERSVNK0EXidMPTN7CjdUeqw4jJzn07+cx9n2FwbDDVoYiIiMhhlKCLxGmxJrl3N97NO/74DtoH21MdioiIiBxCCbpIHJ7oeIIbnr4h1WHM20u9L7Httm387qXfpToUERERmaQEXSQOf3z1j6kOIW7jgXG+8/h3eKXvlVSHIiIiIihBF4nLWbVnpTqEuFX7qsl2ZvPXxr+mOhQRERFBCbpIXE6vPp0jC45MdRhxaR1spcxTxn/v/m9G/aOpDkdERGTJU4IuEgdjDO9a9a5UhxGXZfnL2N25m1H/KF9/+OuL9qFXERGRTKEEXSROZ9edTYW3ItVhzIvX5WXUP8qEnQCgMLsQn9uX4qhERESWNiXoInEqzinm4hUXpzqMeVlRuIL2odfKLN7deDe7O3fzSPsjGkkXERFJEVeqAxDJBB9a9yE8Lg/X7bou1aFE7YTyE3i84/EZ25oHmrn8D5fjNE4Ksgv49qZvs65sXYoiFBERWZo0gi6SAMYYLllxCadXn57qUKK2t29v2Nf81o/b6eZfH/pX/AH/wgUlIiIiStBFEmVqxHlVyapUhxJRjjOHntGesK+fVH4S1bnVPNf9HF9+8MsLF5iIiIgoQRdJpGxnNuc1nJfqMCIq95aHfW1Z/jKe7HoSiwWCizHtG9q3UKGJiIgseUrQRRLsjUe9kfeveT8uk76PeORn54fc7nV5GfGPMBGYmE7Qx/xj3PTsTQsZnoiIyJKmBF0kwUo9pXz0xI9y/rLzUx1KWNnO7JDbjys5bnq03FhDdW41Nb4a/tT4p4UMT0REZElTgi6SJJ8++dOUe8JPJUkla23ENs92P0v3SDctgy10Huykf6x/ASITERERJegiSVLqKeX2i2/ns6d8lhxnTqrDmWFkYiRim1H/KCP+YLsJO8Ej7Y8kOywRERFBddBFksqb5eXy4y7nzJozub/1fnbt38WLPS9SkF3Ak51PRtzfYRw05DewqmQVDuOgfaidp7uexmDIzcql3FtOYXYh+dn59Iz08FLvS3QNd0Xst3e0N+Zz+a8n/4uza88my5kV874iIiISPSXoIgugPr+ey/Mv5/LjLp/edtuLt9E/1s/q0tX0j/bTOdzJ/a3380DrA5R7y7lq3VVsqt9EvnvmA53+gJ+ADTDqH8Xn9s061iu9r/CVB7/CYx2PzRmTx+kBoCK3go6DHRHP4YWeFxgPjCtBFxERSTITzVzUhbZ+/Xr76KOPpjoMkZTYP7SfEk8JLsf83z9ba3n2wLP8/Lmf80LPC7zc+zJ+G9+CQwbDw5c/jMfliasfEZF0ZIzZZa1dn+o4REAj6CJppyK3Iu4+jDGsKl3FNWdeA8DA2AA3PXcT33vie/Puc23ZWiXnIiIiC0APiYosAXnuPK5adxWfWv+pefexrmxdAiMSERGRcDSCLrKEvHPlOxkPjPPzZ3/OgZEDUe+X7cymIb8hiZGJiIjIFI2giywhxhjet+Z93Pj6G6nx1US1z/vXvJ/73noflx5zaZKjExEREVCCLrIk1efXc/sbb+dDx3+IqtyqsO1eV/c6PnLCR/BmeRcwOhERkaVNVVxElrjxwDh7Duzhl3t+ye2v3E5RdhFvPOqNrCxdyQUNF2CMSXWIIiJJpyoukk6UoIvItK7hLgrcBap1LiJLjhJ0SSd6SFREppV6SlMdgoiIyJKnOegiIiIiImlECbqIiIiISBpRgi4iIiIikkaUoIuIiIiIpBEl6CIiIiIiaUQJuoiIiIhIGlGCLiIiIiKSRpSgi4iIiIikESXoIiIiIiJpRAm6iIiIiEgaUYIuIiIiIpJGlKCLiIiIiKQRJegiIiIiImlECbqIiIiISBpRgi4iIiIikkaUoIuIiIiIpBEl6CIiIiIiaUQJuoiIiIhIGlGCLiIiIiKSRpSgi4iIiIikESXoIiIiIiJpRAm6iIiIiEgaUYIuIiIiIpJGlKCLiIiIiKQRJegiIiIiImlECbqIiIiISBpRgi4iIiIikkaUoIuIiIiIpBFjrU11DLMYYzqBxjAvlwJdCxhOutH5L+3zB12DpX7+oGuw1M8fdA2Scf4N1tqyBPcpMi9pmaDPxRjzqLV2farjSBWd/9I+f9A1WOrnD7oGS/38QddgqZ+/ZD5NcRERERERSSNK0EVERERE0shiTNCvT3UAKabzl6V+DZb6+YOuwVI/f9A1WOrnLxlu0c1BFxERERHJZItxBF1EREREJGMpQRcRERERSSNpkaAbY95ijHnGGBMwxqw/ZHuJMeZeY8ygMea7h+3zVmPM7sn9vjlH358zxrxkjHneGHNBMs8jHvO8BpcZY56avA53GWNKQ/SbZYz5n8l2zxljPrcQ5xOrZJ3/ZLu1xpgHJ/t/yhiTk+zziVUyz3+ybf1kH59K5nnEI4m/A+cbY3ZNtttljNm0EOcTqyT/DmTkfdAYk2eMeeKQry5jzLdC9JuR98Foz3+ybdrfByG512CyfdrfC0UgTRJ04GngTcB9h20fAf4ZmPGLZIwpAa4FzrXWrgIqjDHnHt6pMWYl8DZgFbAF+L4xxpn48BMi1mvgAv4TeJ21di2wG7g6RL9vAbKttWuAk4APGGOWJTTyxEjK+U+2+zlw1eS/lXOA8UQHnwDJ+v8/5TrgjwmLNjmSdQ26gIsmfwfeBfwswXEnSrJ+BzL2PmitHbDWHj/1RXCBu9+G6Dcj74PRnv8iug9C8v4NTFkM90KR9EjQrbXPWWufD7F9yFq7g+Av5qGWAy9Yazsnf74HuCRE128AfmWtHbXWvgq8BJySwNATZh7XwEx+5RpjDJAPtIXqerKNC/AAY0B/QoNPgCSe/2Zgt7X2ycn+Dlhr/YmNPn5JPH+MMW8EXgGeSWzUiZWsa2CtfdxaO7X9GSDHGJOd2Ojjl8R/A5l8H5xmjFkBlAP3h+qazLwPTotw/oviPghJvQaL5l4oAmmSoM/DS8CxxphlkzfcNwJ1IdrVAM2H/NwyuW3Rs9aOAx8EniL4R3klcEOIprcAQ0A70AT8P2tt90LFmSwxnP/RgDXG/MkY85gx5tMLGGbSRHv+xphc4DPAVxY0wAUQw7+BQ10CPG6tHU1yeEkXw/ln7H3wMJcBv7ahS5Nl5H3wMHOdf0beB0MIew0y+V4omWnBEnRjzD3GmKdDfL0h1r6stT0E/zD9muA75b3ARKjDhto91uMlSiKvgTEmi+A1OAGoJvjxdqh5lacA/sk2RwD/aIxZPv+zmL8Unb8LOAO4fPK/F4eaDrUQUnT+XwGus9YOxhV8gqToGky1XwX8G/CBeYYftxSdf8beBw/zNuCXYV7LyPvgYeY6/7S5D0LKrkFa3QtFInEt1IGstecluL/bgdsBjDFXErz5Hq6FmSPrtYSZBrAQEnwNjp/s82UAY8zNwGdDtHs7cNfkaFuHMeYBYD3Bj/kWVIrOvwX4P2tt12S7PwAnAn9JYCxRSdH5nwq82QQfpC4EAsaYEWvtd0O0TboUXQOMMbXAbcA7p9qnQgp/BzL1PgiAMWYd4LLW7grTJFPvg0BU558290FI2TVIq3uhSCSLdYoLxpjyyf8WAR8CfhSi2e+Btxljso0xRwArgEcWLsqkagVWGmPKJn8+H3guRLsmYJMJygU2AHsWKMZkivb8/wSsNcZ4J6dDnQ08u0AxJlNU52+tPdNau8xauwz4FvD1DPqDFNU1MMYUAncCn7PWPrCA8SVbtL8DmXwfnHIZ4UdOIXPvg1MinX+m3gcPNec1yPB7oWQia23Kv4CLCb7DHwX2A3865LW9QDcwONlm5eT2XxK8wTwLvO2Q9tuBrx7y8xeAl4Hngden+lwTfA2uIvgHeTfBTxNKDr8GgA/4DcGHYp4F/inV57qQ5z/58xWT5/808M1Un+tCn/8h/XwZ+FSqz3WhrwHwRYLzj5845Ks81ee7kP8GyOD74ORrrwDHHtbXkrgPRnP+kz+n/X0w2dfgkO1pfS/Ul76stRhrUzYVUUREREREDrNop7iIiIiIiGQiJegiIiIiImlECbqIiIiISBpRgi4iIiIikkaUoIuIiIiIpBEl6CIiIiIiaUQJuoiIiIhIGvn/ATIHjasNHS/ZAAAAAElFTkSuQmCC\n",
      "text/plain": [
       "<Figure size 1440x864 with 1 Axes>"
      ]
     },
     "metadata": {
      "needs_background": "light"
     },
     "output_type": "display_data"
    }
   ],
   "source": [
    "nbhood.plot(\n",
    "            figsize=(20,12),   #size of the plot (a bit bigger than the default)\n",
    "            column = 'region',   # column that defines the color of the dots\n",
    "            legend = True,     # add a legend           \n",
    "            legend_kwds={\n",
    "               'loc': 'upper right',\n",
    "               'bbox_to_anchor':(1.3,1)\n",
    "            }                  # this puts the legend to the side\n",
    ") "
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.8.5"
  },
  "toc": {
   "base_numbering": 1,
   "nav_menu": {},
   "number_sections": true,
   "sideBar": true,
   "skip_h1_title": false,
   "title_cell": "Table of Contents",
   "title_sidebar": "Contents",
   "toc_cell": false,
   "toc_position": {},
   "toc_section_display": true,
   "toc_window_display": false
  }
 },
 "nbformat": 4,
 "nbformat_minor": 4
}