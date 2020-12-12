---
description: 'En savoir plus sur : pragma bss_seg'
title: bss_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.bss_seg
- bss_seg_CPP
helpviewer_keywords:
- pragmas, bss_seg
- bss_seg pragma
ms.assetid: 755f0154-de51-4778-97d3-c9b24e445079
ms.openlocfilehash: e7a2cf73f8ab542755e5f6e0183896ce8e64be2a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300877"
---
# <a name="bss_seg-pragma"></a>bss_seg, pragma

Spécifie la section (segment) dans laquelle les variables non initialisées sont stockées dans le fichier objet (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma bss_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)**\
> **#pragma bss_seg (** { **Push**  |  **pop** } [ **,** *identificateur* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Paramètres

**souleve**\
Facultatif Place un enregistrement sur la pile interne du compilateur. Un **Push** peut avoir un *identificateur* et un *nom de section*.

**roulant**\
Facultatif Supprime un enregistrement du haut de la pile interne du compilateur. Une **liste déroulante** peut avoir un *identificateur* et un *nom de section*. Vous pouvez dépiler plusieurs enregistrements à l’aide d’une seule commande **pop** en utilisant l' *identificateur*. La *section-Name* devient le nom de la section BSS active après le pop.

*identificateur*\
Facultatif En cas d’utilisation avec **Push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’elle est utilisée avec **pop**, la directive dépile les enregistrements de la pile interne jusqu’à ce que l' *identificateur* soit supprimé. Si l' *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

*« section-Name »*\
Facultatif Nom d’une section. Lorsqu’elle est utilisée avec **pop**, la pile est dépilée et la *section-Name* devient le nom de la section BSS active.

*« section-Class »*\
Facultatif Ignoré, mais inclus pour la compatibilité avec les versions de Microsoft C++ antérieures à la version 2,0.

## <a name="remarks"></a>Notes

Une *section* dans un fichier objet est un bloc de données nommé qui est chargé en mémoire en tant qu’unité. Une *section BSS* est une section qui contient des données non initialisées. Dans cet article, les termes *segment* et *section* ont la même signification.

La directive **bss_seg** pragma indique au compilateur de placer tous les éléments de données non initialisés à partir de l’unité de traduction dans une section BSS nommée *section-Name*. Dans certains cas, l’utilisation de **bss_seg** peut accélérer les temps de chargement en regroupant les données non initialisées dans une section. Par défaut, la section BSS utilisée pour les données non initialisées dans un fichier objet est nommée `.bss` . Une **bss_seg** directive pragma sans paramètre *de nom de section* rétablit la valeur du nom de la section BSS pour les éléments de données non initialisés suivants `.bss` .

Les données allouées à l’aide du pragma **bss_seg** ne conservent aucune information sur son emplacement.

Pour obtenir la liste des noms qui ne doivent pas être utilisés pour créer une section, consultez [/section](../build/reference/section-specify-section-attributes.md).

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), les fonctions ([code_seg](../preprocessor/code-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).

Vous pouvez utiliser l’application [DUMPBIN.EXE](../build/reference/dumpbin-command-line.md) pour afficher les fichiers objets. Les versions de DUMPBIN pour chaque architecture cible prise en charge sont incluses dans Visual Studio.

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
