---
title: "Conversions depuis les types intégraux non signés | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 15e1bc61e9b15293290098b9414642d8edf46707
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="conversions-from-unsigned-integral-types"></a>Conversions depuis les types intégraux non signés
Un entier non signé est converti en entier non signé ou signé plus court en tronquant les bits de poids fort, ou en entier non signé ou signé plus long par extension zéro (consultez le tableau [Conversions de types intégraux non signés](#_clang_table_4..3)).  
  
 Lorsque la valeur ayant le type intégral est rétrogradée en entier signé plus petit, ou qu'un entier non signé est converti en son entier signé correspondant, la valeur est inchangée si elle peut être représentée dans le nouveau type. Toutefois, la valeur change si le bit de signe est défini, comme dans l'exemple suivant.  
  
```  
int j;  
unsigned short k = 65533;  
  
j = k;  
printf_s( "%hd\n", j );   // Prints -3  
```  
  
 Si elle ne peut pas être représentée, le résultat est défini par l'implémentation. Consultez [Conversions de cast de type](../c-language/type-cast-conversions.md) pour obtenir plus d'informations sur la façon dont le compilateur Microsoft C gère la rétrogradation des entiers. La conversion en entier ou la conversion de type de l'entier provoque le même comportement.  
  
 Les valeurs non signées sont converties de manière à conserver leur valeur et ne sont pas représentables directement en C. La seule exception est une conversion de `unsigned long` en **float** qui, au maximum, perd les bits de poids faible. Sinon, la valeur est conservée, signée ou non signée. Lorsqu'une valeur de type intégral est convertie en valeur flottante et que la valeur est en dehors de la plage qui peut être représentée, le résultat n'est pas défini. (Consultez [Stockage des types de base](../c-language/storage-of-basic-types.md) pour plus d'informations sur la plage des types intégraux et à virgule flottante.)  
  
 Le tableau suivant répertorie les conversions de types intégraux non signés.  
  
### <a name="conversions-from-unsigned-integral-types"></a>Conversions depuis les types intégraux non signés  
  
|De|Pour|Méthode|  
|----------|--------|------------|  
|`unsigned char`|`char`|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|  
|`unsigned char`|**short**|Extension zéro|  
|`unsigned char`|**long**|Extension zéro|  
|`unsigned char`|**unsigned short**|Extension zéro|  
|`unsigned char`|`unsigned long`|Extension zéro|  
|`unsigned char`|**float**|Convertir en **long**. Convertir **long** en **float**|  
|`unsigned char`|**double**|Convertir en **long**. Convertir **long** en **double**|  
|`unsigned char`|`long double`|Convertir en **long**. Convertir **long** en **double**|  
|**unsigned short**|`char`|Conserver l'octet de poids faible|  
|**unsigned short**|**short**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|  
|**unsigned short**|**long**|Extension zéro|  
|**unsigned short**|`unsigned char`|Conserver l'octet de poids faible|  
|**unsigned short**|`unsigned long`|Extension zéro|  
|**unsigned short**|**float**|Convertir en **long**. Convertir **long** en **float**|  
|**unsigned short**|**double**|Convertir en **long**. Convertir **long** en **double**|  
|**unsigned short**|`long double`|Convertir en **long**. Convertir **long** en **double**|  
|`unsigned long`|`char`|Conserver l'octet de poids faible|  
|`unsigned long`|**short**|Conserver le mot de poids faible|  
|`unsigned long`|**long**|Conserver le modèle binaire. Le bit de poids fort devient un bit de signe|  
|`unsigned long`|`unsigned char`|Conserver l'octet de poids faible|  
|`unsigned long`|**unsigned short**|Conserver le mot de poids faible|  
|`unsigned long`|**float**|Convertir en **long**. Convertir **long** en **float**|  
|`unsigned long`|**double**|Convertir directement en **double**|  
|`unsigned long`|`long double`|Convertir en **long**. Convertir **long** en **double**|  
  
 **Section spécifique à Microsoft**  
  
 Pour le compilateur Microsoft 32 bits C, le type `unsigned int` équivaut au type `unsigned long`. La conversion d'une valeur `unsigned int` s'effectue de la même façon que la conversion de `unsigned long`. Les conversions de valeurs `unsigned long` en **float** ne sont pas exactes si la valeur convertie est supérieure à la valeur **long** signée positive maximale.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Conversions d’assignation](../c-language/assignment-conversions.md)
