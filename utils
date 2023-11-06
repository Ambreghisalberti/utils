import numpy as np
import pandas as pd

def is_monotonic(a:np.array)->bool:
    nbr_increasing_values = (a[1:]>=a[:-1]).sum()
    if nbr_increasing_values == 0:
        return True # The array is decreasing
    elif nbr_increasing_values == len(a)-1:
        return True # The array is increasing
    else:
        return False # The array is not monotonic

def intersect(df1:pd.DataFrame,df2:pd.DataFrame)->(pd.DataFrame,pd.DataFrame):
    df1 = df1[df1.index.isin(df2.index)]
    df2 = df2[df2.index.isin(df1.index)]    
    return df1,df2


def sequences(df,time_resolution=np.timedelta64(1,'m')):

    df = df.sort_index()     # We need the dataset to be ordered chronologically (assuming that the index is the time)
    indices = df.index.values
    jump_indices = (indices[1:] - indices[:-1]) > time_resolution
    
    end_sequences = np.append(indices[:-1][jump_indices] , indices[-1])
    start_sequences = np.array([indices[0]]+list(indices[1:][jump_indices]))
    sequences_length = end_sequences-start_sequences

    return sequences_length,start_sequences
