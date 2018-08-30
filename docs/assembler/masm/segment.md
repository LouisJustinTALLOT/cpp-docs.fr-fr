---
title: SEGMENT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f5defce11b611f23b67e5e44ac1b9d406f73c0ae
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210417"
---
# <a name="segment"></a>SEGMENT
Définit un segment de programme appelé *nom* segment d’attributs  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>Paramètres  
 *align*  
 La plage d’adresses de mémoire à partir de laquelle une adresse de début pour le segment peut être sélectionnée. Le type d’alignement peut prendre l’une des opérations suivantes :  
  
|Aligner le Type|Adresse de départ|  
|----------------|----------------------|  
|**BYTE**|Adresse d’octets disponible suivant.|  
|**WORD**|Adresse de word disponible suivant (2 octets par word).|  
|**DWORD**|Prochaine adresse disponible mot double (4 octets par mot double).|  
|**PARA**|Adresse de paragraphe disponible suivant (16 octets par paragraphe).|  
|**PAGE**|Adresse de page disponible suivant (256 octets par page).|  
|**Aligner**(*n*)|Suivant disponible *n*adresse des octets th. Consultez la section Notes pour plus d’informations.|  
  
 Si ce paramètre n’est pas spécifié, **PARA** est utilisé par défaut.  
  
 *combine*  
 **PUBLIC**, **STACK**, **commune**, **mémoire**, **à**<em>adresse</em>, **Privé**  
  
 *use*  
 **USE16**, **USE32**, **FLAT**  
  
 `characteristics`  
 **INFORMATIONS**, **lire**, **écrire**, **EXECUTE**, **partagé**, **NOPAGE**, **NOCACHE**, et **ignorer**  
  
 Ceux-ci sont pris en charge uniquement pour COFF et correspondent aux caractéristiques de section COFF de nom similaire (par exemple, **partagé** correspond à IMAGE_SCN_MEM_SHARED). LECTURE définit l’indicateur IMAGE_SCN_MEM_READ. L’indicateur en lecture seule obsolète a provoqué la section Effacer l’indicateur IMG_SCN_MEM_WRITE. Le cas échéant `characteristics` sont définis, les caractéristiques par défaut ne sont pas utilisés et les indicateurs spécifiée par le programmeur sont en vigueur.  
  
 `ALIAS(` `string` `)`  
 Cette chaîne est utilisée en tant que nom de la section dans l’objet COFF émis.  Crée plusieurs sections portant le même nom externe, avec des noms de segment MASM distincts.  
  
 Non pris en charge avec **/omf**.  
  
 `class`  
 Indique comment segments doivent être combinés et classés dans le fichier assemblé. Les valeurs standard sont, `'DATA'`, `'CODE'`, `'CONST'` et `'STACK'`  
  
## <a name="remarks"></a>Notes  
 Pour `ALIGN(n)`, `n` peut être n’importe quel puissance de 2 à partir de 1 à 8192 ; pas pris en charge avec **/omf**.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)