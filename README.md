# Powerful--Python-Functions-for-Data-Science
Created a class which has a set of dynamic functions which every data scientist uses on a daily basis.

drop_nan_col: Drop columns which has more missing rows using the threshold operator
drop_zero_var_col (for numeric): Drop all the columns with 0 variance
drop_zero_car_col (for categorical): Drops categorical columns with same levels, such as a column with all 'yes' values
drop_high_levels (for categorical): This function will eliminate all the columns has a lot of levels based on threshold
replace_missing
num_value: User decides with what values they want to replace the missing numerical values.This value can be mean median mode or zero
cat_val: User decides with what values they want to replace the missing numerical values. This value can be mode or 'unknown'
encode_target: Encodes the class label if class column is categorical. If class column is numerical just return the same dataframe without doing anything.Do not forget that clas label might have more than 2 levels (yes and no is two levels). Target levels can be agree, stringly agree, disagree strongly disagree, neutral (5 levels)
transform: Transforms numerical values in a way that it will increase model accuracy.
       Transformations: {'asis','log','exp','sqrt','pow2'}
create_dummies: Creates dummy variables for categorical variables
