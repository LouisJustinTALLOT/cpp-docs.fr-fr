---
title: bss_seg | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77d234acdc02a2fefeca45ca0a925603e0ff9984
ms.sourcegitcommit: 80fc7b0452aafa36b0c915cbd29c75e1ffa25630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003557"
---
# <a name="bssseg"></a>bss_seg

Spécifie le segment où les variables non initialisées sont stockées dans le fichier .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma bss_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Paramètres

**push**<br/>
(Facultatif) Place un enregistrement sur la pile interne du compilateur. Un *pu*sh * peut avoir un *identificateur* et *segment-name*.

**pop**<br/>
(Facultatif) Supprime un enregistrement à partir du haut de la pile interne du compilateur.

*identifier*<br/>
(Facultatif) Lorsqu’il est utilisé avec **push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. *identificateur* permet à plusieurs enregistrements à dépiler avec une seule **pop** commande. Lorsqu’il est utilisé avec **pop**, la directive dépile les enregistrements de la pile interne jusqu'à ce que *identificateur* est supprimé ; si *identificateur* est introuvable sur la pile interne, rien n’est dépilés.

*« segment-name »*<br/>
(Facultatif) Le nom d’un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et *segment-name* devient le nom de segment actif.

*« segment-class »*<br/>
(Facultatif) Inclus pour la compatibilité avec C++ antérieures à la version 2.0. Elle est ignorée.

## <a name="remarks"></a>Notes

. Fichiers obj peuvent être affichés avec le [dumpbin](../build/reference/dumpbin-command-line.md) application. Le segment par défaut dans le fichier .obj pour les données non initialisées est .bss. Dans certains cas l’utilisation de **bss_seg** peut accélérer les temps de chargement en regroupant les données non initialisées en une seule section.

**bss_seg** sans paramètres réinitialise le segment à .bss.

Données allouées en utilisant le **bss_seg** pragma ne conserve aucune information concernant leur emplacement.

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), fonctions ([code_seg](../preprocessor/code-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).

Consultez [/SECTION](../build/reference/section-specify-section-attributes.md) pour obtenir la liste des noms que vous ne devez pas utiliser lors de la création d’une section.

## <a name="example"></a>Exemple

```cpp
// pragma_directive_bss_seg.cpp
int i;                     // stored in .bss
#pragma bss_seg(".my_data1")
int j;                     // stored in .my_data1

#pragma bss_seg(push, stack1, ".my_data2")
int l;                     // stored in .my_data2

#pragma bss_seg(pop, stack1)   // pop stack1 from stack
int m;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
