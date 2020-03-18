---
title: code_seg (pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 65d702273593dc7fba68cc040f700b01a2c5e4a7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446474"
---
# <a name="code_seg-pragma"></a>code_seg (pragma)

Spécifie la section de texte (segment) où les fonctions sont stockées dans le fichier objet (. obj).

## <a name="syntax"></a>Syntaxe

> **#pragma code_seg (** ["*section-Name*" [ **,** "*section-Class*"]] **)** \
> **#pragma code_seg (** { **Push** | **pop** } [ **,** *identifier* ] [ **,** "*section-Name*" [ **,** "*section-Class*"]] **)**

### <a name="parameters"></a>Paramètres

\ **Push**
Facultatif Place un enregistrement sur la pile interne du compilateur. Un **Push** peut avoir un *identificateur* et un *nom de section*.

\ **pop**
Facultatif Supprime un enregistrement du haut de la pile interne du compilateur. Une **liste déroulante** peut avoir un *identificateur* et un *nom de section*. Vous pouvez dépiler plusieurs enregistrements à l’aide d’une seule commande **pop** en utilisant l' *identificateur*. La *section-Name* devient le nom de la section de texte active après le pop.

*identificateur*\
Facultatif En cas d’utilisation avec **Push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’elle est utilisée avec **pop**, la directive dépile les enregistrements de la pile interne jusqu’à ce que l' *identificateur* soit supprimé. Si l' *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

«*section-Name*» \
Facultatif Nom d’une section. Lorsqu’elle est utilisée avec **pop**, la pile est dépilée et la *section-Name* devient le nom de la section de texte active.

«*section-Class*» \
Facultatif Ignoré, mais inclus pour la compatibilité avec les versions C++ de Microsoft antérieures à la version 2,0.

## <a name="remarks"></a>Notes

Une *section* dans un fichier objet est un bloc de données nommé qui est chargé en mémoire en tant qu’unité. Une *section de texte* est une section qui contient du code exécutable. Dans cet article, les termes *segment* et *section* ont la même signification.

La directive **code_seg** pragma indique au compilateur de placer tout le code d’objet suivant à partir de l’unité de traduction dans une section de texte nommée *section-Name*. Par défaut, la section de texte utilisée pour les fonctions dans un fichier objet est nommée `.text`. Une **code_seg** directive pragma sans paramètre de *nom de section* réinitialise le nom de la section de texte pour que le code d’objet suivant soit `.text`.

La directive **code_seg** pragma ne contrôle pas le placement du code objet généré pour les modèles instanciés. Il ne contrôle pas non plus le code généré implicitement par le compilateur, comme les fonctions membres spéciales. Pour contrôler ce code, nous vous recommandons d’utiliser à la place l’attribut [__declspec (code_seg (...))](../cpp/code-seg-declspec.md) . Elle vous permet de contrôler le placement de tout le code d’objet, y compris le code généré par le compilateur.

Pour obtenir la liste des noms qui ne doivent pas être utilisés pour créer une section, consultez [/section](../build/reference/section-specify-section-attributes.md).

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), les données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).

Vous pouvez utiliser [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) pour afficher les fichiers objets. Les versions de DUMPBIN pour chaque architecture cible prise en charge sont incluses dans Visual Studio.

## <a name="example"></a>Exemple

Cet exemple montre comment utiliser la directive **code_seg** pragma pour contrôler où le code objet est placé :

```cpp
// pragma_directive_code_seg.cpp
void func1() {                  // stored in .text
}

#pragma code_seg(".my_data1")
void func2() {                  // stored in my_data1
}

#pragma code_seg(push, r1, ".my_data2")
void func3() {                  // stored in my_data2
}

#pragma code_seg(pop, r1)      // stored in my_data1
void func4() {
}

int main() {
}
```

## <a name="see-also"></a>Voir aussi

[code_seg (__declspec)](../cpp/code-seg-declspec.md)\
[Directives pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
