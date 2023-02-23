1. modify the path of input
"""
root_path = "D:\GithubRepository\PARA\Clus/20220911/test\Clus-DoC Results"
file_list = [
    "ROI_1_non_cluster_Ch1.xls",
    "ROI_1_non_cluster_Ch2.xls",
    "ROI_2_non_cluster_Ch1.xls",
    "ROI_2_non_cluster_Ch2.xls"
]
"""
root path is for the input data
file_list is for the data name list
result will be generated into a sub-folder in root_path named "after_col_mark"

2. modify parameter
line 21-25:
"""
    # group data by class column and get total count and count of values greater than 0.4 for each group
    grouped = df.groupby(["ClusterID"])
    select1 = grouped.agg(Col1=("DOC", lambda x: len(x) >= 10))
    # Col2 is a new column name
    select2 = grouped.agg(Col2=("DOC", lambda x: sum(x >= 0.4) > 10))
"""
change the number 10 to any other filter number x for selecting a co-localized group which has x points' doc > than 0.4

3. how to run this script
left click in the empty space of the folder
conda activate clus
python find_ColCluster.py 
# tips :  input several front letters such as  "fi" and tap "table buttom" on keyboard , this can help input the fullname automatic 

or run this code in an IDE pycharm