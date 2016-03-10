##Huevo Programming Language
###Specification v0.1


**Goals**:

- Useful for chefs professional and amateur
- Universal (i18n)
- Human and machine readable
- Abstraction layers


**Some ideas**:

- Scope
- Name
- Inheritance?
- Composable?
- Hierarchical data-types
- Translations/i18n
- Id (UUID based on Name and Scope)
- Media (urls: links)
- Metadata
	- Nutritional
	- Comments /Free text / Annotations 
- Quantities / Units




Two basic entities:

- **Ingredients**: Unprocessed food. Organizing hierarchically it's origin and parts (inheritance?), i18n, and linked with media
- **Tools**: Tools used for cooking, serving, everything that intervines in the process and it is not food.
- **Steps**: Functions that accept ingredients, tools or recipes as parameters and 

And then two complex entities:

- **Libraries**: A collection of Ingredient definitions to be used in the recipes
- **Recipes**: The combination of ingredients via steps and using tools, the result can be used as another ingredient (Should they be considered steps in themselves?)



This is some Huevo code

	{	"type": "recipe"
		"name": "lazos_con_pesto"
		"scope": "home.italian"
		"libraries": 
		["huevo", "pastas_gallo", "carbonell"],		
		"ingredients":[
			{"name":"queso",
			 "type":"huevo.producto_elaborado.lacteo.parmesano.rallado",
			 "quantity":"60:gram"},
			 					
			 {"name":"pesto",
			 "type":"home.italian.sauces.pesto",
			 "quantity":"150:gram"}, 
			 
			{"name":"lazos",
			 "type":"pastas_gallo.pajaritas_vegetales",
			 "quantity":"200:gram"},
			 
			 {"name":"aceite",
			 "type":"carbonell.aceite_virgen_extra",
			 "quantity":"40:mililitre"}, 
			 
			{"name":"sal",
			 "type":"huevo.rocas.inertes.sal",
			 "quantity":"10:gram"},
			 
			 {"name":"agua",
			 "type":"huevo.inerte.agua",
			 "quantity":"1,5:litre"}, 			 			 
		],
		"tools":[
			{"name":"olla",
			 "type":"huevo.recipiente.acero.inox.olla",
			 "quantity":"1:unit"
			},
			{"name":"colador",
			 "type":"huevo.utensilio.acero.inox.colador",
			 "quantity":"1:unit"
			},
			{"name":"platos",
			 "type":"huevo.recipiente.ceramica.hondo.plato",
			 "quantity":"2:unit"
			},			
		],
		"steps": [

			{"function":"boil",
			 "time": "10:minute",
 			 "temperature": "100:celsius",
			 "tool": "olla",			 
			 "ingredients":["agua","sal"],
			 "result":["hervido"]
			},

			{"function":"boil",
			 "time": "8:minute",
 			 "temperature": "100:celsius",
			 "tool": "olla",			 
			 "ingredients":["hervido","lazos"],
			 "result":["cocido"]
			},
			
			{"function":"strain",
			 "time": "20:second",
			 "tool": "colador",			 
			 "ingredients":["cocido"],
			 "result":["pasta_cocida","agua_cocida"]
			},
			
			{"function":"pour",
			 "time": "20:second",
			 "ingredients":["pasta_cocida","aceite"],
			 "result":["pasta_cocida_aceite"]
			},
			
			{"function":"serve",
			 "time": "20:second",
			 "tool": "plato",			 
			 "ingredients":["pasta_cocida_aceite"],
			 "result":["plato_pasta"]
			},
			
			{"function":"pour",
			 "time": "20:second",		 
			 "ingredients":["plato_pasta","pesto"],
			 "result":["plato_pasta_pesto"]
			},
			
			{"function":"scatter",
			 "time": "20:second",		 
			 "ingredients":["queso","plato_pasta_pesto"],
			 "result":["plato_final"]
			},									
		],
		"result":"plato_final"
	
	}