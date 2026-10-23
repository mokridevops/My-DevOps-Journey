
# AWS Cloud Front

<img width="1873" height="861" alt="image" src="https://github.com/user-attachments/assets/a7710a90-a8db-4798-9078-8b2306abeb43" />

Origin should be: Elastic Load Balancer

since, we can access load balance with HTTPS :

<img width="1642" height="782" alt="image" src="https://github.com/user-attachments/assets/0e826a86-3fd5-45db-9c90-1ece6e452016" />

<img width="1551" height="773" alt="image" src="https://github.com/user-attachments/assets/94d7dada-e5e4-4566-9e2e-3c5d0a66df76" />

<img width="1516" height="706" alt="image" src="https://github.com/user-attachments/assets/146db89a-cd8a-4757-a679-66df74930765" />


<img width="1736" height="782" alt="image" src="https://github.com/user-attachments/assets/2e96aff0-aaf4-4b7b-9368-41ac42fe28a2" />


we only allow Get, Head, options

<img width="1474" height="717" alt="image" src="https://github.com/user-attachments/assets/89c6f49a-1137-4830-a6f3-f944c2c3c0aa" />

<img width="1497" height="765" alt="image" src="https://github.com/user-attachments/assets/1529ef4c-a19b-46c1-8b37-34bd34698eeb" />

<img width="1851" height="760" alt="image" src="https://github.com/user-attachments/assets/04cf491c-5001-4f7e-a8a2-c99350c4eaf9" />

<img width="1855" height="775" alt="image" src="https://github.com/user-attachments/assets/bf3a2c70-67b8-4c1f-ab6d-83ba0c0fe796" />

<img width="1897" height="965" alt="image" src="https://github.com/user-attachments/assets/dbcce345-6891-4550-9531-524574cafec3" />

<img width="1833" height="896" alt="image" src="https://github.com/user-attachments/assets/252acaa4-aecd-4137-a283-884d9d920a76" />

we need to cache these kinds of items

<img width="1309" height="886" alt="image" src="https://github.com/user-attachments/assets/fb720d51-f99d-4c7a-943b-58ccce447b1f" />

in the create behaviour

path: /media/* -> what ever coming in this path -> cache it

<img width="1235" height="925" alt="image" src="https://github.com/user-attachments/assets/567080fa-1ccd-4a0b-9ea6-e16197353fd7" />


<img width="1428" height="866" alt="image" src="https://github.com/user-attachments/assets/7f6452b1-3b64-40ed-808b-64f5aae1a021" />

<img width="1884" height="947" alt="image" src="https://github.com/user-attachments/assets/852285a9-824c-4ca0-ac4d-814fe51eca2b" />

so, what ever request formats you wanted to be Cached - path based - for those you have to create behaviors

<img width="1890" height="972" alt="image" src="https://github.com/user-attachments/assets/377d42e5-dc81-4f76-9bac-d51ba2eb9ee9" />

<img width="1871" height="839" alt="image" src="https://github.com/user-attachments/assets/834aba6d-d1af-4e24-8e04-a0bbc176fb0b" />

if no behavior is matching, then it will go to default -> Caching Disabled

<img width="1886" height="570" alt="image" src="https://github.com/user-attachments/assets/51947d9c-f21f-4139-8c9f-6df642cb2e69" />

<img width="1892" height="556" alt="image" src="https://github.com/user-attachments/assets/4cd1a1b4-227c-4750-86ff-52f87216c650" />
















