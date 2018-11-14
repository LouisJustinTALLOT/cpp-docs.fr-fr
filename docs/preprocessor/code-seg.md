---
title: code_seg
ms.date: 11/04/2016
f1_keywords:
- code_seg_CPP
- vc-pragma.code_seg
helpviewer_keywords:
- pragmas, code_seg
- code_seg pragma
ms.assetid: bf4faac1-a511-46a6-8d9e-456851d97d56
ms.openlocfilehash: 80edcb709073021ccf024aaf14c9a914bd8d8939
ms.sourcegitcommit: 31a2a9845f5e1d35ab054906d8cdc6582a5220bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51597701"
---
# <a name="codeseg"></a>code_seg
Spécifie le segment de texte dans lequel les fonctions sont stockées dans un fichier .obj.

## <a name="syntax"></a>Syntaxe

```
#pragma code_seg( [ [ { push | pop }, ] [ identifier, ] ] [ "segment-name" [, "segment-class" ] )
```

### <a name="parameters"></a>Paramètres

**push**<br/>
(Facultatif) Place un enregistrement sur la pile interne du compilateur. Un **push** peut avoir un *identificateur* et *segment-name*.

**pop**<br/>
(Facultatif) Supprime un enregistrement à partir du haut de la pile interne du compilateur.

*identifier*<br/>
(Facultatif) Lorsqu’il est utilisé avec **push**, assigne un nom à l’enregistrement sur la pile interne du compilateur. Lorsqu’il est utilisé avec **pop**, dépile les enregistrements de la pile interne jusqu'à ce que *identificateur* est supprimé ; si *identificateur* est introuvable sur la pile interne, rien n’est dépilé.

*identificateur* permet à plusieurs enregistrements à dépiler avec un seul **pop** commande.

«*segment-name*»<br/>
(Facultatif) Le nom d’un segment. Lorsqu’il est utilisé avec **pop**, la pile est dépilée et *segment-name* devient le nom de segment de texte active.

«*segment-classe*»<br/>
(Facultatif) Ignoré, mais inclus pour la compatibilité avec les versions antérieures à la version 2.0 de C++.

## <a name="remarks"></a>Notes

Le **code_seg** directive pragma ne contrôle pas l’emplacement de code objet généré pour les modèles instanciés, ni le code généré de manière implicite par le compilateur, par exemple, les fonctions membres spéciales. Nous vous recommandons d’utiliser le [__declspec(code_seg(...)) ](../cpp/code-seg-declspec.md) attribut au lieu de cela, car il vous donne contrôler l’emplacement de tout le code objet. Cela comprend le code généré par le compilateur.

Un *segment* dans un .obj fichier est un bloc nommé de données qui sont chargés en mémoire en tant qu’unité. Un *segment de texte* est un segment qui contient le code exécutable. Dans cet article, les termes du contrat *segment* et *section* sont utilisés indifféremment.

Le **code_seg** directive pragma indique au compilateur de placer tout prochain code objet à partir de l’unité de traduction dans un segment de texte nommé *segment-name*. Par défaut, le segment de texte utilisé pour les fonctions d'un fichier .obj est nommé ".text".

Un **code_seg** directive pragma sans paramètres réinitialise le nom de segment de texte pour le prochain code objet en ".Text".

Vous pouvez utiliser le [DUMPBIN. EXE](../build/reference/dumpbin-command-line.md) application pour afficher les fichiers .obj. Version de DUMPBIN pour chaque architecture cible prise en charge est incluse avec Visual Studio.

## <a name="example"></a>Exemple

Cet exemple montre comment utiliser le **code_seg** directive de pragma pour contrôler l’emplacement du code objet :

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

Pour obtenir la liste des noms qui ne doit pas être utilisé pour créer une section, consultez [/SECTION](../build/reference/section-specify-section-attributes.md).

Vous pouvez également spécifier des sections pour les données initialisées ([data_seg](../preprocessor/data-seg.md)), données non initialisées ([bss_seg](../preprocessor/bss-seg.md)) et les variables const ([const_seg](../preprocessor/const-seg.md)).

## <a name="see-also"></a>Voir aussi

[code_seg (__declspec)](../cpp/code-seg-declspec.md)<br/>
[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)