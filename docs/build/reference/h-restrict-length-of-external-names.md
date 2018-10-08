---
title: -H (limiter la longueur des noms externes) | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /h
dev_langs:
- C++
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c4881ba20e999b13e2a7841161a775eac69638f6
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861016"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Limiter la longueur des noms externes)

Obsolète. Limite la longueur des noms externes.

## <a name="syntax"></a>Syntaxe

> **/H**<em>nombre</em>

## <a name="arguments"></a>Arguments

*Nombre*<br/>
Spécifie la longueur maximale des noms externes autorisés dans un programme.

## <a name="remarks"></a>Notes

Par défaut, la longueur des noms (publics) externes est limitée à 2 047 caractères. Cela est vrai pour les programmes C et C++. À l’aide de **/H** peut seulement diminuer la longueur maximale autorisée d’identificateurs, pas l’augmenter. Un espace entre **/H** et *nombre* est facultatif.

Si un programme contient des noms externes dépasse *nombre*, les caractères supplémentaires sont ignorés. Si vous compilez un programme sans **/H** et si un identificateur contient plus de 2 047 caractères, le compilateur générera [erreur irrécupérable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

La longueur limite inclut n’importe quel créé par le compilateur trait de soulignement (**\_**) ou signe arobase (**\@**). Ces caractères font partie de l’identificateur et occupent un emplacement particulier.

- Le compilateur ajoute un trait de soulignement (**\_**) aux noms modifiés par la `__cdecl` (valeur par défaut) et `__stdcall` conventions d’appel et un préfixe arobase (**\@** ) aux noms modifiés par la `__fastcall` convention d’appel.

- Le compilateur ajoute des informations de taille d’argument aux noms modifiés par la `__fastcall` et `__stdcall` conventions d’appel et ajoute les informations de type aux noms C++.

Vous trouverez peut-être **/H** utiles :

- Lorsque vous créez des programmes portables ou de plusieurs langues.

- Lorsque vous utilisez des outils qui imposent des limites sur la longueur des identificateurs externes.

- Lorsque vous souhaitez limiter la quantité d’espace qui utilisent des symboles dans une version debug.

L’exemple suivant montre comment l’utilisation **/H** réellement peut introduire des erreurs si les longueurs des identificateurs sont trop limitées :

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

Vous devez également être prudent lorsque vous utilisez le **/H** option en raison des identificateurs prédéfinis du compilateur. Si la longueur maximale de l’identificateur est trop petite, certains identificateurs prédéfinis sera non résolues, ainsi que certains bibliothèque les appels de fonction. Par exemple, si le `printf` fonction est utilisée et l’option **/H5** est spécifiée au moment de la compilation, le symbole **_prin** sera créé pour référencer `printf`, et il sera introuvable dans la bibliothèque.

Utilisation de **/H** est incompatible avec [/GL (Whole Program Optimization)](../../build/reference/gl-whole-program-optimization.md).

Le **/H** option est déconseillée depuis Visual Studio 2005 ; les limites de longueur maximale ont été augmentées et **/H** n’est plus nécessaire. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options déconseillées et supprimées du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
