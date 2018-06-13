---
tags: How-To DbUnit Java Testing
---
```
<dataset>
    <TABLE1 COL1="value" COL2="[NULL]"/>
    <TABLE1 COL1="[NULL]" COL2="value"/>
</dataset>    
```

```
    ReplacementDataSet replacementDataSet = new ReplacementDataSet(
     new FlatXmlDataSetBuilder().build(new File("dbSourceFileLocation")));
    );
    replacementDataSet.addReplacementObject("[NULL]", null);
    // continue usual datasource setup
```
