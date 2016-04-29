#Algorithmic recipes

During the workshop: *Algorithmic Kitchen* with Luis Rodil-Fernández algorithmic recipes were compiled by scraping and sorting a BBC recipe database.
See underneath 2 delicious examples:

##Algorithmic Chicken Soup

![Algorithmic Chicken and Potato Soup](Chicken-and-Potato-Soup.png)

Input:

    import re
    import operator
    
    verbMap = {}
    adjMap = {}
    otherMap = {}
    
    o = store.find(Recipe, Recipe.name.like(u'%onions%'))
    for r in o:
        for i in r.ingredients:
            #print i.name
            l = i.name.split()
            for j in l:
                s = re.sub('[^A-Za-z]+', '', j)
                if s.endswith('ly'):
                    if s in adjMap:
                        adjMap[s] += 1
                    else:
                        adjMap[s] = 1
                elif s.endswith('ed') or s.endswith('ing'):
                    if s in verbMap:
                        verbMap[s] += 1
                    else:
                        verbMap[s] = 1
                else:
                    if s in ingMap:
                        ingMap[s] += 1
                    else:
                        ingMap[s] = 1
                 
                  
    #for key, value in ingMap.iteritems():
    #    print key, value
        
    sortedAdj = sorted(adjMap.keys(), key=lambda key: 
    adjMap[key], reverse=True)
    for ing in sortedAdj:
      print ing
    print "------"
    sortedVerbs = sorted(verbMap.keys(), key=lambda key: 
    verbMap[key], reverse=True)
    for ing in sortedVerbs:
        print ing
    print "------"
    sortedIng = sorted(ingMap.keys(), key=lambda key: 
    ingMap[key], reverse=True)
    for ing in sortedIng:
        print ing


Output:
* freshly chopped onions
* finely sliced olives
* thinly peeled potatos
* roughly halved chicken
* thickly grated garlic

The End...Eat!

##HOT Algorithms

![Algorithmic Sichuan Cucumber Salad](SichuanCucumber.png)

    FROM recipes 
    WHERE 
    Description LIKE “%spicy%”
    AND description LIKE “%salad%”;
 
        ID 1026
        u’Chunky bacon and cucumber salad’
        u’A spicy Sichuan-style salad of cucumber 
        and fried bacon.’
             
            Serves 6
            PT30M
            PT10M

    re = store.find(Recipe, Recipe.id == 1026).any()
    print “name”, re.name
    #print “photo url”, fs.photo.url
    print re.ingredients.count()

    print re.ingredients.count()

    for i in re.ingredients:
    print i.name

Output:

name Chunky bacon and cucumber salad
3 tbsp groundnut oil
18 long dried chillies 
6 tsp Sichuan peppercorns 
3 whole star anise (optional)
300g smoked lardons, cut into 1cm/½in thick pieces
3 red chilli, de-seeded, finely chopped
3 tbsp Shaoxing rice wine or dry sherry
6 tbsp clear rice vinegar or cider vinegar
6 tbsp toasted sesame oil
600g cucumber, halved lengthways, de-seeded and sliced into 1cm/½in thick wedges 
1 pinch sea salt
3 pinches dried chilli flakes
3 tbsp lime juice
3 tbsp chilli oil 
3 small handful fresh coriander leaves, roughly chopped dry-roasted peanuts (optional)

%%sqlite cookbook.db
SELECT id, ordinal, description FROM preparations WHERE recipe_id = 1026 ORDER BY ordinal;

id	ordinal	description
8652	1		u’Heat a wok until smoking and add the groundnut oil, then add the dried chillies and 
Sichuan peppercorns. Stir fry for a few seconds, or until fragrant. ‘
8653	2		u’Add the star anise (if using), bacon lardons and chilli and stir fry for 
2-3 minutes, or until the lardons have turned golden-brown at the edges.’
8654	3		u’Add the rice wine or sherry, vinegar and sesame oil and stir-fry for a few seconds, 
then add the cucumber and stir-fry for a few more seconds.’
8655	4		u’Season with sea salt, dried chilli flakes and lime juice, stirring well.’
8656	5		u’Pile the stir-fry onto a serving plate, drizzle over the chilli oil, garnish 
with the chopped coriander, sprinkle over some peanuts, if using, and serve 
immediately.’


See our scrapes here: [pantry.algorithmickitchen.org:8000/](http://pantry.algorithmickitchen.org:8000/tree)

