
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


now, it got deployed:

<img width="1853" height="928" alt="image" src="https://github.com/user-attachments/assets/d1a427f4-fa21-4221-9392-17a11be25fc2" />

now we will access by saying: roboshop-cdn.daws90s.shop

<img width="1513" height="622" alt="image" src="https://github.com/user-attachments/assets/b4d6dee9-cc84-4ef4-86c1-3d3db7bdc0da" />

it is not pulling the roboshop page, lets create Route53 record:

### For CDN we need to create a Route53 record

## We can create CloudFront only in US-EAST-1 region, no other regions we can create cloudfronts

<img width="1853" height="926" alt="image" src="https://github.com/user-attachments/assets/296397b9-5f40-4e24-a880-9f8e390a3603" />

<img width="1726" height="900" alt="image" src="https://github.com/user-attachments/assets/a486f34a-27cf-4d26-a2f3-db40d78d975d" />

<img width="1832" height="886" alt="image" src="https://github.com/user-attachments/assets/43992586-b707-4e46-8787-e07f248e680b" />

<img width="1850" height="937" alt="image" src="https://github.com/user-attachments/assets/2e04e593-b1df-4898-add8-e61db386a526" />

<img width="1884" height="956" alt="image" src="https://github.com/user-attachments/assets/51845760-ccf0-4a2c-ae91-2fd2c77a6d17" />



<img width="1863" height="943" alt="image" src="https://github.com/user-attachments/assets/9f3fcfd4-3b00-45b2-a06f-074d776e3d7d" />

<img width="1664" height="745" alt="image" src="https://github.com/user-attachments/assets/819e6356-2906-4b99-afb9-4e36a15400db" />

still the roboshop-cdn.daws-90s.shop is not working, let us check if there are any geo location restrictions enabled:


<img width="1853" height="937" alt="image" src="https://github.com/user-attachments/assets/5e40f592-c9e3-416a-97ee-1f48280f195a" />

lets verify Origin settings:

<img width="1844" height="842" alt="image" src="https://github.com/user-attachments/assets/c905b4ab-84e3-4d6d-a7e3-cc1696ce9de3" />

<img width="1258" height="918" alt="image" src="https://github.com/user-attachments/assets/c480aecb-6667-42e3-a8ac-c6c2c465f1a7" />

<img width="1437" height="832" alt="image" src="https://github.com/user-attachments/assets/8064541a-6ae8-4131-b1d1-89ad01c1d11f" />


<img width="1614" height="859" alt="image" src="https://github.com/user-attachments/assets/fbd67ac6-7792-4d73-a41e-24a5b7ad02f1" />

<img width="1390" height="835" alt="image" src="https://github.com/user-attachments/assets/a5979b7f-4b70-47fb-9933-ef57179f2498" />


now, we are able to access roboshop website through CDN:

<img width="1846" height="766" alt="image" src="https://github.com/user-attachments/assets/7e0c2fe2-b325-4a49-b137-448c29791ea4" />


<img width="1883" height="933" alt="image" src="https://github.com/user-attachments/assets/fc639abc-353c-48e2-a560-334a789a4599" />

now, we can see it is coming from CloudFront

so, we give the following URL to public:

roboshop-cdn.daws90s.shop

<img width="1892" height="565" alt="image" src="https://github.com/user-attachments/assets/e0e10656-b6ec-4ca1-93a7-2e34901a801b" />

<img width="1869" height="894" alt="image" src="https://github.com/user-attachments/assets/53c4dc64-b4fe-4ce9-8442-38da8ffbf1b3" />



### Invalidations:

<img width="1877" height="957" alt="image" src="https://github.com/user-attachments/assets/2d3585fc-a498-4636-8f83-f19ca895162f" />

if media file changes, we can come here to Invalidations and create an invalidation

<img width="1870" height="873" alt="image" src="https://github.com/user-attachments/assets/ebdbe286-b29a-4752-9d8a-eea38aa850d7" />

<img width="1868" height="660" alt="image" src="https://github.com/user-attachments/assets/a17646ce-fb43-4539-bc94-e4e689c8e8d2" />

once, invalidation is created, AWS will remove the content of media from its edge locations, in your domain in that path

<img width="1873" height="621" alt="image" src="https://github.com/user-attachments/assets/f1231e0b-02df-48f1-8173-7077a02d6b1d" />

Now, we do this through Terraform:

<img width="1522" height="982" alt="image" src="https://github.com/user-attachments/assets/bcedda05-a517-4c4e-aa37-ac63ba247d2f" />

<img width="1849" height="175" alt="image" src="https://github.com/user-attachments/assets/4e17196d-7d89-41a3-a49b-8ae007c7c309" />

<img width="1811" height="260" alt="image" src="https://github.com/user-attachments/assets/ce6e8476-dbb8-432c-a84b-40943ecc4f26" />

if we give 100 - it is taking after 10 - as it is a string, not a number

whenever I want to delete in reverse order:

<img width="1746" height="343" alt="image" src="https://github.com/user-attachments/assets/08829d2e-f997-4146-bf97-e6917b260d60" />


Terraform has some official open source modules, which we can use too:

<img width="1528" height="827" alt="image" src="https://github.com/user-attachments/assets/27f9ef35-8a85-4a87-b7b3-d28c0377b174" />

<img width="1197" height="962" alt="image" src="https://github.com/user-attachments/assets/c0063636-6ecc-4459-8133-64b28a76328d" />

<img width="1257" height="947" alt="image" src="https://github.com/user-attachments/assets/e49af053-666e-463e-b150-0a2bb7687328" />

<img width="1827" height="940" alt="image" src="https://github.com/user-attachments/assets/cfe1d17f-0883-4c38-8427-f26d175782d4" />

-- what is the problem if we use these?

If we use, these, and in between if there is any problem, then we have to wait until those guys give us a solution.  Since, we are also terraform engineers, we also know Terraform - we can just build it from scratch

<img width="1892" height="968" alt="image" src="https://github.com/user-attachments/assets/0d6c2b94-111d-4b39-89cb-ee4b08b021d4" />

<img width="1737" height="683" alt="image" src="https://github.com/user-attachments/assets/fdcb11b6-6ee4-48d8-a804-4fd2fb04b944" />

So, it is better to develop - in house terraform modules, we don't need to depend on anyone for any fixes

if we want to use these, we can directly refer these modules and use them:

<img width="1887" height="968" alt="image" src="https://github.com/user-attachments/assets/4da38671-9a50-4181-bbe9-705d6b63a250" />

<img width="1790" height="101" alt="image" src="https://github.com/user-attachments/assets/e172070a-a8ab-4b1e-8de4-51240b5a2a46" />

<img width="1867" height="953" alt="image" src="https://github.com/user-attachments/assets/bdd171c2-c150-460b-aeff-22f95c489fa0" />

we will build our own module

we can give geo restriction - if we want to access certain things from only particular countries, we can give that also

<img width="1867" height="953" alt="image" src="https://github.com/user-attachments/assets/761cc117-a389-4580-8bcd-032b178333cd" />

































































