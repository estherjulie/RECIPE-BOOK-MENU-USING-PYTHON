importjson
import os
defload_recipes():
"""Load recipesfromtheJSONfileifit exists,otherwisereturnanemptylist."""if
os.path.exists('recipes.json'):
with open('recipes.json', 'r') as file:
return json.load(file)
return[]
defsave_recipes(recipes):
"""Save the list of recipes to the JSON
file."""withopen('recipes.json','w')asfile:
json.dump(recipes,file,indent=4)
defadd_recipe(recipes):
"""Prompt the user to input details of a new recipe and add it to the
list."""name = input("Enter the recipe name: ")
ingredients=input("Entertheingredients:")
instructions = input("Enter the instructions: ")
recipes.append({'name':name,'ingredients':ingredients,'instructions':
instructions})
save_recipes(recipes)
print("Recipeadded successfully!")
defview_recipes(recipes):
"""Display all the recipes in the
list."""if not recipes:
print("No recipes found.")
return
for idx, recipe in enumerate(recipes, start=1):
print(f"{idx}. {recipe['name']}")
print(f"Ingredients:{recipe['ingredients']}")
print(f"Instructions:{recipe['instructions']}\n")
defsearch_recipe(recipes):
"""Searchforarecipebynameanddisplayitiffound."""search_na
me = input("Enter the recipe name to search: ").lower()for recipe
in recipes:
ifsearch_nameinrecipe['name'].lower():
print(f"Recipefound:{recipe['name']}")
print(f"Ingredients: {recipe['ingredients']}")
print(f"Instructions:{recipe['instructions']}\n")
return
print("Recipenotfound.")
def main():
"""Main function to display the menu and handle user
choices."""recipes = load_recipes()
whileTrue:
print("\nRecipeBookMenu")
print("1. Add Recipe")
print("2. View Recipes")
print("3.SearchRecipe")
print("4. Exit")
choice = input("Enter your choice: ")
if choice == '1':
add_recipe(recipes)
elif choice == '2':
view_recipes(recipes)
elif choice == '3':
search_recipe(recipes)
elif choice == '4':
break
else:
print("Invalidchoice.Pleasetryagain.")
if _name_ == "_main_":
main() 10
