---
title: Passage de paramètres | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ec0c5b6fe00430c8b08fefdd8781b677004085e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32369355"
---
# <a name="parameter-passing"></a>Passage de paramètres
Les quatre premiers arguments entiers sont passés dans les registres. Valeurs entières sont passées (dans l’ordre de gauche à droite) dans RCX, RDX, R8 et R9. Arguments de cinq ou supérieur sont passés sur la pile. Tous les arguments sont alignés à droite dans les registres. Cela permet l’appelé peut ignorer les bits supérieurs du Registre si besoin d’être et peut accéder uniquement à la partie du Registre nécessaire.  
  
 Les arguments à virgule flottante et double précision sont passés dans XMM0 : XMM3 (jusqu'à 4) avec l’emplacement d’entier (RCX, RDX, R8 et R9) qui serait normalement utilisé pour qu’il soit cardinale emplacement ignorée (voir l’exemple) et vice versa.  
  
 [__m128](../cpp/m128.md) chaînes, tableaux et des types ne sont jamais passés par valeur immédiate mais plutôt un pointeur est passé à la mémoire allouée par l’appelant. Les structures/unions de taille 8, 16, 32 ou 64 bits et __m64 sont passées comme s’ils étaient des entiers de la même taille. Les structures/unions que ces tailles sont passées en tant que pointeur vers la mémoire allouée par l’appelant. Pour ces types d’agrégats passés en tant que pointeur (y compris \__m128), la mémoire temporaire allouée par l’appelant sera alignée sur 16 octets.  
  
 Fonctions intrinsèques qui n’allouent pas d’espace de pile et n’appellent pas d’autres fonctions peuvent utiliser autres registres volatils pour passer des arguments de Registre supplémentaires, car il existe une liaison étroite entre le compilateur et l’implémentation de la fonction intrinsèque. Il s’agit d’une autre possibilité d’améliorer les performances.  
  
 L’appelé est chargé de vider les paramètres de Registre dans leur espace de clichés instantanés, si nécessaire.  
  
 Le tableau suivant résume la façon dont les paramètres sont passés :  
  
|Type de paramètre|Mode de passage|  
|--------------------|----------------|  
|Virgule flottante|4 premiers paramètres - XMM0 à XMM3. Autres sont passés sur la pile.|  
|Entier|4 premiers paramètres - RCX, RDX, R8, R9. Autres sont passés sur la pile.|  
|Agrégats (8, 16, 32 ou 64 bits) et les __m64|4 premiers paramètres - RCX, RDX, R8, R9. Autres sont passés sur la pile.|  
|Agrégats (autres)|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9.|  
|__m128|Par pointeur. 4 premiers paramètres passés comme pointeurs dans RCX, RDX, R8 et R9.|  
  
## <a name="example-of-argument-passing-1---all-integers"></a>Exemple 1 - tous les entiers de passage d’argument  
  
```  
func1(int a, int b, int c, int d, int e);    
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-2---all-floats"></a>Exemple 2 - tous les nombres à virgule flottante de passage d’argument  
  
```  
func2(float a, double b, float c, double d, float e);    
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack  
```  
  
## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Exemple d’argument qui passe 3 - ints mixte et des valeurs en virgule flottante  
  
```  
func3(int a, double b, int c, float d);    
// a in RCX, b in XMM1, c in R8, d in XMM3  
```  
  
## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Exemple d’argument qui passe 4-__m64, \__m128 et des agrégats  
  
```  
func4(__m64 a, _m128 b, struct c, float d);  
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)