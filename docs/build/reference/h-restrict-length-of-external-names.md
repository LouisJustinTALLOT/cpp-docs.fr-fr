---
description: En savoir plus sur:/H (restreindre la longueur des noms externes)
title: /H (Limiter la longueur des noms externes)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 5df4c4765cc4917e6914eab0b4818c34fceea853
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200076"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Limiter la longueur des noms externes)

Action déconseillée. Limite la longueur des noms externes.

## <a name="syntax"></a>Syntaxe

> **/H**<em>nombre</em>

## <a name="arguments"></a>Arguments

*number*<br/>
Spécifie la longueur maximale des noms externes autorisés dans un programme.

## <a name="remarks"></a>Notes

Par défaut, la longueur des noms externes (publics) est de 2 047 caractères. Cela est vrai pour les programmes C et C++. L’utilisation de **/h** peut réduire la longueur maximale autorisée des identificateurs, et ne pas l’augmenter. Un espace entre **/h** et *Number* est facultatif.

Si un programme contient des noms externes d’une longueur supérieure à *Number*, les caractères supplémentaires sont ignorés. Si vous compilez un programme sans **/h** et si un identificateur contient plus de 2 047 caractères, le compilateur génère une [Erreur irrécupérable C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

La limite de longueur comprend tout trait de soulignement de début ( **\_** ) ou de signe () créé par le compilateur **\@** . Ces caractères font partie de l’identificateur et prennent un emplacement significatif.

- Le compilateur ajoute un trait de soulignement de début ( **\_** ) aux noms modifiés par le **`__cdecl`** (par défaut) et les **`__stdcall`** conventions d’appel, et un signe de début ( **\@** ) aux noms modifiés par la **`__fastcall`** Convention d’appel.

- Le compilateur ajoute des informations sur la taille des arguments aux noms modifiés par les **`__fastcall`** **`__stdcall`** conventions d’appel et, et ajoute des informations de type aux noms C++.

Vous pouvez trouver **/h** utile :

- Lorsque vous créez des programmes portables ou multilingues.

- Lorsque vous utilisez des outils qui imposent des limites sur la longueur des identificateurs externes.

- Lorsque vous souhaitez limiter la quantité d’espace utilisée par les symboles dans une version Debug.

L’exemple suivant montre comment l’utilisation de **/h** peut en fait introduire des erreurs si les longueurs des identificateurs sont limitées trop :

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

Vous devez également être prudent lorsque vous utilisez l’option **/h** en raison des identificateurs de compilateur prédéfinis. Si la longueur maximale de l’identificateur est trop petite, certains identificateurs prédéfinis sont non résolus, ainsi que certains appels de fonction de bibliothèque. Par exemple, si la `printf` fonction est utilisée et que l’option **/H5** est spécifiée au moment de la compilation, le symbole **_prin** sera créé pour référencer `printf` , et cela ne sera pas trouvé dans la bibliothèque.

L’utilisation de **/h** est incompatible avec [/GL (optimisation de l’ensemble du programme)](gl-whole-program-optimization.md).

L’option **/h** est dépréciée depuis Visual Studio 2005 ; les limites de longueur maximale ont été augmentées et **/h** n’est plus nécessaire. Pour obtenir la liste des options du compilateur déconseillées, consultez **Options du compilateur déconseillées et supprimées** dans [Options du compilateur classées par catégorie](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
