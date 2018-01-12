---
title: "Déclarations et définitions (C++) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea0f8210993e494cbd4795a2c4cf7c6c0afa8aa2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="declarations-and-definitions-c"></a>Déclarations et définitions (C++)
Déclarations introduisent des noms dans un programme, par exemple les noms de variables, des espaces de noms, fonctions et classes. Les déclarations spécifient également les informations de type ainsi que d'autres caractéristiques de l'objet qui est déclaré. Un nom doit être déclaré avant de pouvoir être utilisé ; en C++, le point auquel un nom est déclaré détermine s'il est visible par le compilateur. Vous ne pouvez pas faire référence à une fonction ou une classe qui est déclarée au niveau d’un point ultérieur dans l’unité de compilation ; Vous pouvez utiliser *pré-déclarations* pour contourner cette limitation.  
  
 Définitions de spécifient le code ou les données décrites par le nom. Le compilateur a besoin de la définition afin d'allouer de l'espace de stockage pour l'élément déclaré.  
  
## <a name="declarations"></a>Déclarations  
 Une déclaration introduit un ou plusieurs noms dans un programme. Les déclarations peuvent se produire plusieurs fois dans un programme. Par conséquent, les classes, les structures, les types énumérés et d'autres types définis par l'utilisateur peuvent être déclarés pour chaque unité de compilation. Sur cette déclaration multiple, la contrainte est que toutes les déclarations doivent être identiques. Les déclarations servent également de définitions, sauf lorsque la déclaration :  
  
1.  est un prototype de fonction (une déclaration de fonction sans corps de fonction) ;  
  
2.  contient le spécificateur `extern`, mais ne contient aucun initialiseur (objets et variables) ni corps de fonction (fonctions). Cela signifie que la définition n'est pas nécessairement dans l'unité de traduction actuelle et donne une liaison externe au nom.  
  
3.  est celle d'une donnée membre static dans une déclaration de classe ;  
  
     Les données membres de classe static sont des variables discrètes partagées par tous les objets de la classe. Elles doivent être définies et initialisées en dehors de la déclaration de classe. (Pour plus d’informations sur les classes et membres de classe, consultez [Classes](../cpp/classes-and-structs-cpp.md).)  
  
4.  est une déclaration de nom de classe qui n'est pas suivie par une définition, par exemple `class T;` ;  
  
5.  est une instruction `typedef`.  
  
 Voici des exemples de déclarations qui sont également des définitions :  
  
```  
// Declare and define int variables i and j.  
int i;  
int j = 10;  
  
// Declare enumeration suits.  
enum suits { Spades = 1, Clubs, Hearts, Diamonds };  
  
// Declare class CheckBox.  
class CheckBox : public Control  
{  
public:  
            Boolean IsChecked();  
    virtual int     ChangeState() = 0;  
};  
```  
  
 Voici des déclarations qui ne sont pas des définitions :  
  
```  
  
extern int i;  
char *strchr( const char *Str, const char Target );  
```  
  
 Un nom est considéré comme déclaré immédiatement après son déclarateur mais avant son initialiseur (facultatif). Pour plus d’informations, consultez [Point de déclaration](../cpp/point-of-declaration-in-cpp.md).  
  
 Déclarations se produisent dans un *étendue*. La portée contrôle la visibilité du nom déclaré et la durée de l'objet défini, le cas échéant. Pour plus d’informations sur la façon dont les règles de portée interagissent avec les déclarations, consultez [étendue](../cpp/scope-visual-cpp.md).  
  
 Une déclaration d’objet est également une définition, sauf si elle contient la `extern` spécificateur de classe de stockage décrite dans [classes de stockage](storage-classes-cpp.md). Une déclaration de fonction est également une définition, sauf si elle est un prototype. Un prototype est un en-tête de fonction sans le corps de fonction qui le définit. La définition d'un objet entraîne l'allocation de stockage et les initialisations appropriées pour cet objet.  
  
## <a name="definitions"></a>Définitions  
 Une définition est une spécification unique d'un objet, d'une variable, d'une fonction, d'une classe ou d'un énumérateur. Les définitions devant être uniques, un programme peut contenir une seule définition d'un élément de programme donné. Il peut exister une correspondance plusieurs-à-un entre les déclarations et les définitions. Voici deux cas dans lesquels un élément de programme peut être déclaré et non défini :  
  
1.  Une fonction est déclarée, mais elle n'est jamais référencée avec un appel de fonction ou une expression qui prend l'adresse de la fonction.  
  
2.  Une classe est uniquement utilisée d'une façon qui ne requiert pas que sa définition soit connue. Toutefois, la classe doit être déclarée. Le code suivant illustre ce type de situation :  
  
    ```  
    // definitions.cpp  
    class WindowCounter;   // Forward declaration; no definition  
  
    class Window  
    {  
       // Definition of WindowCounter not required  
       static WindowCounter windowCounter;  
    };  
  
    int main()  
    {  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base](../cpp/basic-concepts-cpp.md)   
 [Point de déclaration](../cpp/point-of-declaration-in-cpp.md)