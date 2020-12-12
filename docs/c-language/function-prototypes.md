---
description: 'En savoir plus sur : prototypes de fonction'
title: Prototypes de fonctions
ms.date: 11/04/2016
helpviewer_keywords:
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
ms.openlocfilehash: d8e83e68daaa610387f3a23c06ad5ee49a8b3944
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151838"
---
# <a name="function-prototypes"></a>Prototypes de fonctions

Une déclaration de fonction précède la définition de fonction et spécifie le nom, le type de retour, la classe de stockage et d’autres attributs d’une fonction. Pour être un prototype, la déclaration de fonction doit également établir des types et des identificateurs pour les arguments de la fonction.

## <a name="syntax"></a>Syntaxe

*déclaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*DECLARATION-Specifiers* *attribute-SEQ*<sub>OPT</sub> *init-declarator-List*<sub>OPT</sub> **;**

/\**attribute-SEQ*<sub>OPT</sub> est spécifique à Microsoft\*/

*declaration-specifiers* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

*init-declarator-list* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-List*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*déclarateur* **=** *initialiseur*

*déclarateur*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointeur*<sub>OPT</sub> *direct-declarator*

*direct-declarator*:/ \* un déclarateur de fonction \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator***(***Parameter-type-list***)**   / \* New-style declarator      \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;déclarateur *direct-declarator***(***identifier-List*<sub>OPT</sub> **)**  / \* -déclarateur de style obsolète    \*/

Le prototype a la même forme que la définition de fonction, sauf qu'il se termine par un point-virgule juste après la parenthèse fermante et qu'il n'a par conséquent aucun corps. Dans les deux cas, le type de retour doit correspondre à celui spécifié dans la définition de fonction.

Les principales utilisations des prototypes de fonction sont les suivantes :

- Ils établissent le type de retour pour les fonctions qui retournent des types autres que **`int`** . Bien que les fonctions qui retournent **`int`** des valeurs ne requièrent pas de prototypes, les prototypes sont recommandés.

- Sans prototypes complets, les conversions standard sont réalisées mais aucune tentative n'est effectuée pour vérifier le type ou le nombre d'arguments avec le nombre de paramètres.

- Les prototypes sont utilisés pour initialiser des pointeurs vers des fonctions avant que celles-ci soient définies.

- La liste des paramètres sert à vérifier la correspondance des arguments dans l'appel de fonction avec les paramètres de la définition de fonction.

Le type converti de chaque paramètre détermine l'interprétation des arguments que l'appel de fonction place sur la pile. Une incompatibilité de type entre un argument et un paramètre peut provoquer l’interprétation erronée des arguments dans la pile. Par exemple, sur un ordinateur 16 bits, si un pointeur 16 bits est passé comme argument, puis déclaré en tant que **`long`** paramètre, les 32 premiers bits de la pile sont interprétés comme un **`long`** paramètre. Cette erreur crée des problèmes non seulement avec le **`long`** paramètre, mais avec tous les paramètres qui le suivent. Vous pouvez détecter les erreurs de ce genre en déclarant des prototypes complets pour toutes les fonctions.

Un prototype établit les attributs d'une fonction de sorte que les appels à la fonction qui précèdent sa définition (ou qui se produisent dans d'autres fichiers sources) puissent être vérifiés afin de détecter les incompatibilités de type d'argument et de type de retour. Par exemple, si vous spécifiez le **`static`** spécificateur de classe de stockage dans un prototype, vous devez également spécifier la **`static`** classe de stockage dans la définition de fonction.

Les déclarations de paramètre complètes ( `int a` ) peuvent être mélangées avec des déclarateurs abstraits ( **`int`** ) dans la même déclaration. Par exemple, la déclaration suivante est autorisée :

```C
int add( int a, int );
```

Le prototype peut inclure à la fois le type et un identificateur pour chaque expression passée comme argument. Toutefois, ces identificateurs ont une portée uniquement jusqu'à la fin de la déclaration. Le prototype peut également refléter le fait que le nombre d'arguments est variable ou qu'aucun argument n'est passé. Sans une telle liste, les incompatibilités risquent de ne pas être révélées et le compilateur ne pourra pas générer les messages de diagnostic les concernant. Pour plus d’informations sur la vérification du type, consultez [Arguments](../c-language/arguments.md).

La portée de prototype dans le compilateur C Microsoft est maintenant conforme à la norme ANSI lors de la compilation avec l'option de compilateur **/Za**. Cela signifie que si vous déclarez **`struct`** une **`union`** balise ou dans un prototype, la balise est entrée au niveau de cette portée plutôt qu’au niveau de la portée globale. Par exemple, lors de la compilation avec **/Za** à des fins de conformité ANSI, vous ne pouvez jamais appeler cette fonction sans obtenir une erreur d'incompatibilité de type :

```C
void func1( struct S * );
```

Pour corriger votre code, définissez ou déclarez **`struct`** ou **`union`** au niveau de la portée globale avant le prototype de fonction :

```C
struct S;
void func1( struct S * );
```

Sous **/Ze**, l’étiquette est toujours entrée au niveau de la portée globale.

## <a name="see-also"></a>Voir aussi

[Fonctions](../c-language/functions-c.md)
