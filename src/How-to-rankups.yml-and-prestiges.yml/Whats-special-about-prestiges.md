# What's Special About Prestiges?  
## Prestige-Based Requirements  
### You can specify requirements by prestige in your rankups!  
For example, if you had ranks A and B, and the prestiges P1 and P2, you might have this in your rankups.yml:  
```yaml
a: # heading:
  rank: 'A'
  next: 'B'
  requirements:
    default: # used when a player hasn't prestiged
      - 'money 100'
    p1: # used in p1
      - 'money 200'
    p2: # used in p2
      - 'money 300'
```
When a player successfully ranks up from A to B, one of three things will happen:  
1. They will be charged $100 when they have not yet prestiged  
2. They will be charged $200 when they have prestiged to p1  
3. They will be charged $300 when they have prestiged to p2

This is the most significant difference between [`prestiges: false` and `prestiges: true`](https://github.com/okx-code/Rankup3/blob/master/src/main/resources/config.yml#L41-L47)
