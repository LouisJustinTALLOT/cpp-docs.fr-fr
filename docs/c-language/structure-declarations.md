---
title: Déclarations de structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7d305b2bc74455abd6fdbcfb29ed7ef4103bf19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391898"
---
# <a name="structure-declarations"></a>Déclarations de structure
Une déclaration de structure désigne un type et spécifie une séquence de valeurs variables (appelées membres ou champs de la structure) qui peuvent avoir des types. Un identificateur facultatif, appelé balise indique le nom du type de structure et peut être utilisé dans les références suivantes au type structure. Une variable de ce type structure contient la séquence entière définie par ce type. Les structures en C sont semblables aux types appelés enregistrements dans d'autres langages.  
  
## <a name="syntax"></a>Syntaxe  
 *struct-or-union-specifier* :  
 *struct-or-union identifier* opt **{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union* :  
 **struct**  
  
 **union**  
  
 *struct-declaration-list* :  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 Le contenu de structure est défini comme  
  
 *struct-declaration* :  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list* :  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list* :  
 *struct-declarator*  
  
 *struct-declarator-list* **,** *struct-declarator*  
  
 *struct-declarator* :  
 `declarator`  
  
 La déclaration d'un type structure ne met pas de côté l'espace pour une structure. C'est uniquement un modèle pour les déclarations suivantes de variables de structure.  
  
 Un *identifier* (étiquette) défini peut être utilisé pour faire référence à un type structure défini ailleurs. Dans ce cas, *struct-declaration-list* ne peut pas être répété tant que la définition est visible. Les déclarations de pointeurs vers les structures et typedefs pour les types de structure peuvent utiliser l’étiquette de structure avant que le type de structure ne soit défini. Toutefois, la définition de structure doit être produite avant toute utilisation réelle de la taille des champs. C'est une définition incomplète du type et de la balise de type. Pour que cette définition soit terminée, une définition de type doit apparaître plus loin dans la même portée.  
  
 *struct-declaration-list* spécifie les types et les noms des membres de structures. Un argument *struct-declaration-list* contient une ou plusieurs déclarations de variable ou de champ de bits.  
  
 Chaque variable déclarée dans *struct-declaration-list* est définie comme membre du type structure. Les déclarations de variables dans *struct-declaration-list* ont la même forme que d’autres déclarations de variables décrites dans cette section, mais les déclarations ne peuvent pas contenir des spécificateurs ou initialiseurs de classe de stockage. Les membres de structures peuvent avoir tout type de variable sauf le type `void`, un type incomplet ou un type de fonction.  
  
 Un membre ne peut pas être déclaré comme ayant le type de la structure dans laquelle il apparaît. Toutefois, un membre peut être déclaré comme pointeur vers le type structure dans lequel il apparaît tant que le type structure a une balise. Cela vous permet de créer des listes de structures liées.  
  
 Les structures respectent la même portée que les autres identificateurs. Les identificateurs de structure doivent être distingués des autres étiquettes de structure, d’union et d’énumération ayant la même visibilité.  
  
 Chaque *struct-declaration* présent dans *struct-declaration-list* doit être unique dans la liste. Toutefois, les noms d’identificateur présents dans un argument *struct-declaration-list* ne doivent pas être distingués des noms de variables ordinaires ou des identificateurs présents dans d’autres listes de déclaration de structure.  
  
 Les structures imbriquées sont également accessibles comme si elles avaient été déclarées au niveau de la portée du fichier. Par exemple, supposons cette déclaration :  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 ces déclarations sont toutes deux valides :  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent des déclarations de structure :  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 La structure `employee` a trois membres : `name`, `id` et `class`. Le membre `name` est un tableau de 20 éléments et `id` et `class` sont des membres simples avec `int` et le type **long**, respectivement. L'identificateur `employee` est l'identificateur de structure.  
  
```  
struct employee student, faculty, staff;  
```  
  
 Cet exemple définit trois variables de structure : `student`, `faculty` et `staff`. Chaque structure possède la même liste de trois membres. Les membres sont déclarés comme ayant le type structure `employee`, défini dans l'exemple précédent.  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 La structure `complex` possède deux membres avec le type **float**, `x` et `y`. Le type de structure n’a aucune étiquette et est par conséquent sans nom ou anonyme.  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 Les deux premiers membres de la structure sont une variable `char` et un pointeur vers une valeur **float** . Le troisième membre, `next`, est déclaré comme un pointeur vers le type de structure définie (`sample`).  
  
 Les structures anonymes peuvent être utiles lorsque la balise nommée n'est pas nécessaire. C'est le cas lorsqu'une déclaration définit toutes les instances de structure. Exemple :  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 Les structures incorporées sont souvent anonymes.  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Section spécifique à Microsoft**  
  
 Le compilateur autorise un tableau non dimensionné ou un tableau de taille zéro comme dernier membre d'une structure. Cela peut être utile si la taille d'un tableau fixe diffère lorsqu'elle est utilisée dans différentes situations. La déclaration de cette structure ressemble à ceci :  
  
 `struct` *identifier***{** *set-of-declarations* *type array-name***[ ];};**  
  
 Les tableaux non dimensionnés peuvent apparaître uniquement comme dernier membre d'une structure. Les structures contenant des déclarations de tableau non dimensionné peuvent être imbriquées dans d'autres structures tant qu'aucun autre membre n'est déclaré dans une structure englobante. Les tableaux de ces structures ne sont pas autorisés. L'opérateur `sizeof`, une fois appliqué à une variable de ce type ou au type lui-même, suppose 0 pour la taille du tableau.  
  
 Les déclarations de structure peuvent également être spécifiées sans déclarateur lorsqu'elles sont membres d'une autre structure ou union. Les noms de champ sont promus dans la structure englobante. Par exemple, une structure sans nom ressemble à ceci :  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 Pour plus d’informations sur les références de structure, consultez [Membres de structure et d’union](../c-language/structure-and-union-members.md).  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Déclarateurs et déclarations de variable](../c-language/declarators-and-variable-declarations.md)