  - While populating in paginate options => populate: 'Schema Model Name'.
    -  paginateOptions = {
          ...paginateOptions,
          populate: 'CompanyGroup',
        }; 
  - We don't use name of the field in this method like we will use populate: "CompanyGroup" instead of populate: "companyGroups"; like we usually do. 
  - When we use different syntax:
      - paginateOptions = {
          ...paginateOptions,
          populate: [{ path: 'productGroupTemplate' }, { path: 'companyGroups' }],
        }; 
      - you will use the path as the name of the field so this is the difference. 

  - You can use more properties if required like in following example
    - Collection.paginate(query,{
         page : 1,
         limit : 10,
         populate : [
           {
             path : 'refName1',
             select : {field : 1}
           },
           {
             path : 'refName2',
             select : {field : 1}
           }
         ]
      })
