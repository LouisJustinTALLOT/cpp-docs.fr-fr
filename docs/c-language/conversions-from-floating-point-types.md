---
title: "Conversions à partir des types à virgule flottante | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4974edd25d0fcdd8d990b60459517bb1148c74ae
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="conversions-from-floating-point-types"></a>Conversions depuis les types à virgule flottante
Une valeur **float** convertie en valeur **double** ou `long double`, ou une valeur **double** convertie en `long double`, n'entraîne aucune modification de la valeur. Une valeur **double** convertie en valeur **float** est représentée exactement, si possible. La précision peut être perdue si la valeur ne peut pas être représentée exactement. Si le résultat est hors limites, le comportement n'est pas défini. Consultez [Limites sur les constantes à virgule flottante](../c-language/limits-on-floating-point-constants.md) pour la plage de types à virgule flottante.  
  
 Une valeur flottante est convertie en une valeur intégrale en convertissant d'abord en valeur **long**, puis une valeur **long** en valeur intégrale spécifique. La partie décimale de la valeur flottante est ignorée dans la conversion en **long**. Si le résultat est toujours trop grand pour être contenu dans **long**, la conversion n'est pas définie.  
  
 **Section spécifique à Microsoft**  
  
 Lors de la conversion d'un nombre à virgule flottante **double** ou `long double` en un plus petit nombre à virgule flottante, la variable de la virgule flottante est tronquée vers zéro en cas de dépassement de capacité négatif. Un dépassement de capacité provoque une erreur d'exécution. Notez que le compilateur Microsoft C mappe `long double` en type **double**.  
  
 **FIN de la section spécifique à Microsoft**  
  
 Le tableau suivant répertorie les conversions des types de flottant.  
  
### <a name="conversions-from-floating-point-types"></a>Conversions depuis les types à virgule flottante  
  
|De|Pour|Méthode|  
|----------|--------|------------|  
|**float**|`char`|Convertir en **long**. Convertir **long** en `char`|  
|**float**|**short**|Convertir en **long**. Convertir **long** en **short**|  
|**float**|**long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long**, il n'est pas défini.|  
|**float**|**unsigned short**|Convertir en **long**. Convertir **long** en `unsigned` **short**|  
|**float**|`unsigned long`|Convertir en **long**. Convertir **long** en `unsigned` **long**|  
|**float**|**double**|Modifier la représentation interne|  
|**float**|`long double`|Modifier la représentation interne|  
|**double**|`char`|Convertir en **float**. Convertir **float** en `char`|  
|**double**|**short**|Convertir en **float**. Convertir **float** en **short**|  
|**double**|**long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long**, il n'est pas défini.|  
|**double**|**unsigned short**|Convertir en **long**. Convertir **long** en **unsigned short**|  
|**double**|`unsigned long`|Convertir en **long**. Convertir **long** en `unsigned` **long**|  
|**double**|**float**|Représenter comme **float**. Si la valeur **double** ne peut pas être représentée exactement comme **float**, une perte de précision se produit. Si la valeur est trop grande pour être représentée comme **float**, le résultat n'est pas défini.|  
|`long double`|`char`|Convertir en **float**. Convertir **float** en `char`|  
|`long double`|**short**|Convertir en **float**. Convertir **float** en **short**|  
|`long double`|**long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long**, il n'est pas défini.|  
|`long double`|**unsigned short**|Convertir en **long**. Convertir **long** en `unsigned` **short**|  
|`long double`|`unsigned long`|Convertir en **long**. Convertir **long** en `unsigned` **long**|  
|`long double`|**float**|Représenter comme **float**. Si la valeur **double** ne peut pas être représentée exactement comme **float**, une perte de précision se produit. Si la valeur est trop grande pour être représentée comme **float**, le résultat n'est pas défini.|  
|`long double`|**double**|La valeur **long double** est traitée comme **double**.|  
  
 Les conversions de valeurs **float**, **double**, ou `long double` en `unsigned long` ne sont pas exactes si la valeur convertie est supérieure à la valeur **long**.  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions d’assignation](../c-language/assignment-conversions.md)