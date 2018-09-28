---
title: Appels de fonction | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls, about function calls
- function calls
ms.assetid: 2cfa897d-3874-4820-933c-e624f75d1712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8849cd932bd44b5dd7094d05470a4a97f58b08cb
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43755489"
---
# <a name="function-calls"></a>Appels de fonction
Un *appel de fonction* est une expression qui passe le contrôle et des arguments (le cas échéant) à une fonction et qui se présente sous la forme :  
  
*expression* (*expression-list*<sub>opt</sub>)  
  
où *expression* est un nom de fonction ou correspond à une adresse de fonction et où *expression-list* est une liste d'expressions (séparées par des virgules). Les valeurs de ces dernières expressions sont les arguments passés à la fonction. Si la fonction ne retourne pas de valeur, vous la déclarez comme une fonction qui retourne `void`.  
  
Si une déclaration existe avant l'appel de fonction, mais qu'aucune information n'est donnée concernant les paramètres, tous les arguments non déclarés subissent simplement les conversions arithmétiques habituelles.  
  
> [!NOTE]
>  Les expressions figurant dans la liste d'arguments de la fonction peuvent être évaluées dans un ordre quelconque, de sorte que les arguments dont les valeurs peuvent être modifiées par les effets secondaires d'un autre argument ont des valeurs non définies. Le point de séquence défini par l'opérateur d'appel de fonction garantit uniquement que tous les effets secondaires dans la liste d'arguments sont évalués avant que le contrôle passe à la fonction appelée. (Notez que l’ordre dans lequel les arguments font l’objet d’un push dans la pile est une question distincte.) Pour plus d'informations, consultez [Points de séquence](../c-language/c-sequence-points.md).  
  
La seule exigence à respecter dans un appel de fonction est que l’expression avant les parenthèses doit correspondre à une adresse de fonction. Cela signifie qu'une fonction peut être appelée via toute expression de pointeur fonction.  
  
## <a name="example"></a>Exemple  
L'exemple ci-dessous illustre des appels de fonction à partir d'une instruction `switch` :  
  
```  
int main()  
{  
    /* Function prototypes */  
  
    long lift( int ), step( int ), drop( int );  
    void work( int number, long (*function)(int i) );  
  
    int select, count;  
    .  
    .  
    .  
    select = 1;  
    switch( select )   
    {  
        case 1: work( count, lift );  
                break;  
  
        case 2: work( count, step );  
                break;  
  
        case 3: work( count, drop );  
                /* Fall through to next case */  
        default:  
                break;  
    }  
}  
  
/* Function definition */  
  
void work( int number, long (*function)(int i) )  
{  
    int i;  
    long j;  
  
    for ( i = j = 0; i < number; i++ )  
            j += ( *function )( i );  
}  
```  
  
Dans cet exemple, l'appel de fonction dans `main`,  
  
```  
work( count, lift );  
```  
  
passe une variable entière, `count`, et l'adresse de la fonction `lift` à la fonction `work`. Notez que l'adresse de fonction est passée simplement en fournissant l'identificateur de fonction, étant donné qu'un identificateur de fonction correspond à une expression de pointeur. Pour utiliser un identificateur de fonction de cette façon, la fonction doit être déclarée ou définie avant que l'identificateur soit utilisé ; sinon, l'identificateur n'est pas reconnu. Dans ce cas, un prototype pour `work` est fourni au début de la fonction `main`.  
  
Le paramètre `function` figurant dans `work` est déclaré comme étant un pointeur désignant une fonction qui accepte un seul argument `int` et retourne une valeur **long**. Les parenthèses autour du nom du paramètre sont requises. Sans elles, la déclaration spécifierait une fonction retournant un pointeur vers une valeur **long**.  
  
La fonction `work` appelle la fonction sélectionnée à partir de la boucle **for** à l'aide de l'appel de fonction suivant :  
  
```  
( *function )( i );  
```  
  
Un argument, `i`, est passé à la fonction appelée.  
  
## <a name="see-also"></a>Voir aussi  
[Fonctions](../c-language/functions-c.md)