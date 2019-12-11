---
title: SEGMENT
ms.date: 12/06/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: 933e4e42b4b0f9cc979a3e67805d017f723472ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988013"
---
# <a name="segment"></a>SEGMENT

Définit un segment de programme appelé *Name* ayant des attributs de segment

## <a name="syntax"></a>Syntaxe

> *nom* **segment** ⟦**ReadOnly**⟧ ⟦*Aligner*⟧ ⟦*combiner*⟧ ⟦*utiliser*les*caractéristiques*⟧ ⟦ ⟧ **alias (** _String_ **)** ⟦ __'__ *Class* __'__ ⟧ \
> *instructions*\
> **fin** du nom

#### <a name="parameters"></a>Parameters

*align*<br/>
Plage d’adresses mémoire à partir de laquelle une adresse de départ du segment peut être sélectionnée. Le type d’alignement peut être l’un des éléments suivants :

|Aligner le type|Adresse de début|
|----------------|----------------------|
|**BYTE**|Adresse d’octet suivante disponible.|
|**WORD**|Adresse du mot suivant disponible (2 octets par mot).|
|**DWORD**|Adresse du mot double disponible suivant (4 octets par mot double).|
|**Param**|Prochaine adresse du paragraphe disponible (16 octets par paragraphe).|
|**PAGE**|Adresse de la page suivante disponible (256 octets par page).|
|**Aligner**(*n*)|Prochaine adresse disponible *n*ième octets. Pour plus d’informations, consultez la section Notes.|

Si ce paramètre n’est pas spécifié, **para** est utilisé par défaut.

*combiner* (MASM 32 bits uniquement) \
**Public**, **Stack**, **Common**, **Memory**, **à**l'<em>adresse</em>, **privé**

*use* (MASM 32 bits uniquement) \
**USE16**, **USE32**, **FLAT**

*caractéristiques*\
**Info**, **lire**, **écrire**, **exécuter**, **partagé**, **nopage**, **NoCache**et **Ignorer**

Ceux-ci sont pris en charge pour le format COFF uniquement et correspondent aux caractéristiques de la section COFF du même nom (par exemple, **Shared** correspond à IMAGE_SCN_MEM_SHARED). LIRE définit l’indicateur de IMAGE_SCN_MEM_READ. L’indicateur READONLY obsolète a provoqué l’effacement de l’indicateur IMG_SCN_MEM_WRITE par la section. Si des *caractéristiques* sont définies, les caractéristiques par défaut ne sont pas utilisées et seuls les indicateurs spécifiés par le programmeur sont appliqués.

_string_\
Cette chaîne est utilisée comme nom de section dans l’objet COFF émis.  Crée plusieurs sections avec le même nom externe, avec des noms de segment MASM distincts.

Non pris en charge avec **/OMF**.

*class*\
Désigne la manière dont les segments doivent être combinés et classés dans le fichier assemblé. Les valeurs standard sont, `'DATA'`, `'CODE'`, `'CONST'` et `'STACK'`

## <a name="remarks"></a>Notes

Par `ALIGN(n)`, *n* peut être toute puissance de 2 comprise entre 1 et 8192 ; non pris en charge avec **/OMF**.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les directives](directives-reference.md)
