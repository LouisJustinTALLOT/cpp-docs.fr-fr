---
title: data_seg, pragma
ms.date: 08/29/2019
f1_keywords:
- data_seg_CPP
- vc-pragma.data_seg
helpviewer_keywords:
- data_seg pragma
- pragmas, data_seg
ms.assetid: 65c66466-4c98-494f-93af-106beb4caf78
ms.openlocfilehash: f67a9f39695adf5067c61288cf09ea7eb481c7dd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220378"
---
# <a name="data_seg-pragma"></a>data_seg, pragma

Spécifie la section de données (segment) dans laquelle les variables initialisées sont stockées dans le fichier objet (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma data_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma data_seg (** { **Push** | **pop** } [ **,** *identificateur* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Paramètres

**souleve**\
Facultatif Place un enregistrement sur la pile interne du compilateur. Un **Push** peut avoir un *identificateur* et un *nom de section*.

**roulant**\
Facultatif Supprime un enregistrement du haut de la pile interne du compilateur. Une **liste** déroulante peut avoir un *identificateur* et un *nom de section*. Vous pouvez dépiler plusieurs enregistrements à l’aide d’une seule commande **pop** en utilisant l' *identificateur*. La *section-Name* devient le nom de la section de données actives après le pop.

*identificateur*\
Facultatif En cas d’utilisation avec **Push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu’à la suppression de l' *identificateur* . Si l' *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

l' *identificateur* permet à plusieurs enregistrements d’être dépilés à l’aide d’une seule commande **pop** .

*«section-Name»* \
Facultatif Nom d’une section. Lorsqu’elle est utilisée avec **pop**, la pile est dépilée et la *section-Name* devient le nom de la section de données active.

*«section-Class»* \
Facultatif Ignoré, mais inclus pour la compatibilité avec les versions C++ de Microsoft antérieures à la version 2,0.

## <a name="remarks"></a>Notes

Une *section* dans un fichier objet est un bloc de données nommé qui est chargé en mémoire en tant qu’unité. Une *section de données* est une section qui contient des données initialisées. Dans cet article, les termes *segment* et *section* ont la même signification.

La section par défaut dans le fichier. obj pour les variables initialisées est `.data`. Les variables qui ne sont pas initialisées sont considérées comme initialisées à zéro et sont `.bss`stockées dans.

La directive pragma **data_seg** indique au compilateur de placer tous les éléments de données initialisés à partir de l’unité de traduction dans une section de données nommée *section-Name*. Par défaut, la section de données utilisée pour les données initialisées dans un fichier objet `.data`est nommée. Les variables qui ne sont pas initialisées sont considérées comme initialisées à zéro et sont stockées `.bss`dans. Une directive pragma **data_seg** sans paramètre de *nom de section* rétablit le nom de la section de données pour les éléments de `.data`données initialisés suivants sur.

Les données allouées à l’aide de **data_seg** ne conservent aucune information sur leur emplacement.

Pour obtenir la liste des noms qui ne doivent pas être utilisés pour créer une section, consultez [/section](../build/reference/section-specify-section-attributes.md).

Vous pouvez également spécifier des sections pour les variables const ([const_seg](../preprocessor/const-seg.md)), les données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les fonctions ([code_seg](../preprocessor/code-seg.md)).

Vous pouvez utiliser [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) pour afficher les fichiers objets. Les versions de DUMPBIN pour chaque architecture cible prise en charge sont incluses dans Visual Studio.

## <a name="example"></a>Exemples

```cpp
// pragma_directive_data_seg.cpp
int h = 1;                     // stored in .data
int i = 0;                     // stored in .bss
#pragma data_seg(".my_data1")
int j = 1;                     // stored in .my_data1

#pragma data_seg(push, stack1, ".my_data2")
int l = 2;                     // stored in .my_data2

#pragma data_seg(pop, stack1)   // pop stack1 off the stack
int m = 3;                     // stored in .my_data1

int main() {
}
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
