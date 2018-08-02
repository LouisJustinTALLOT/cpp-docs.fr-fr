---
title: Résolution des déclarations ambiguës (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc5b5a2b7d8add493efc144931160afb7d15020
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467877"
---
# <a name="resolving-ambiguous-declarations-c"></a>Résolution des déclarations ambiguës (C++)
Pour exécuter des conversions explicites d'un type en un autre, vous devez utiliser des casts, en spécifiant le nom de type voulu. Certains casts de type entraînent une ambiguïté syntaxique. Le cast de type de style fonction suivant est ambigu :  
  
```cpp 
char *aName( String( s ) );  
```  
  
 Il est difficile de savoir s’il s’agit d’une déclaration de fonction ou une déclaration d’objet avec un cast de style fonction comme initialiseur : il peut déclarer une fonction qui retourne le type `char *` qui prend un argument de type `String`, ou il peut déclarer l’objet `aName` et initialisez-la avec la valeur de `s` cast en type `String`.  
  
 Si une déclaration peut être considérée comme une déclaration de fonction valide, elle est traitée comme telle. Une instruction est examinée pour voir s'il s'agit d'un cast de type de style fonction seulement si ce peut être une déclaration de fonction, c'est-à-dire si elle serait syntaxiquement incorrecte. Par conséquent, le compilateur considère l'instruction comme une déclaration d'une fonction et ignore les parenthèses autour de l'identificateur `s`. En revanche, les instructions :  
  
```cpp 
char *aName( (String)s );  
```  
  
 et  
  
```cpp 
char *aName = String( s );  
```  
  
 sont clairement des déclarations d’objets et une conversion définie par l’utilisateur à partir du type `String` à taper `char *` est appelée pour effectuer l’initialisation de `aName`.  