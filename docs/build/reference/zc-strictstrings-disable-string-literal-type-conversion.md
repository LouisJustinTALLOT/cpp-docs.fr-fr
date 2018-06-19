---
title: '/ Zc : strictstrings (désactiver la conversion de type de littéral chaîne) | Documents Microsoft'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:strictStrings
- strictStrings
dev_langs:
- C++
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7025a4bae2d4a7474cb366b041a3c62f3d7db819
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379937"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (Désactiver la conversion du type de littéral de chaîne)

Quand il est spécifié, le compilateur requiert une conformité de qualification `const` stricte pour les pointeurs initialisés à l'aide de littéraux de chaîne.

## <a name="syntax"></a>Syntaxe

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Notes

Si **/Zc : strictstrings** est spécifié, le compilateur applique le standard C++ `const` qualifications des littéraux de chaîne en tant que type ' tableau de `const char`' ou ' tableau de `const wchar_t`», en fonction de la déclaration. Les littéraux de chaîne sont immuables et une tentative de modification du contenu d'un de ces littéraux entraîne une erreur de violation d'accès au moment de l'exécution. Vous devez déclarer un pointeur de chaîne en tant que `const` pour l'initialiser en utilisant un littéral de chaîne ou utilisez un `const_cast` explicite pour initialiser un pointeur non `const`. Par défaut, ou si **/Zc:strictStrings-** est spécifié, le compilateur n’applique pas le standard C++ `const` qualifications pour les pointeurs de chaîne initialisés à l’aide de littéraux de chaîne.

Le **/Zc : strictstrings** option est désactivée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option du compilateur définit implicitement cette option, mais elle peut être substituée à l’aide de **/Zc:strictStrings-**.

Utilisez le **/Zc : strictstrings** option pour empêcher la compilation de code incorrect. Cet exemple montre comment une simple erreur de déclaration conduit à un incident au moment de l'exécution :

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Lorsque **/Zc : strictstrings** est activé, le même code signale une erreur dans la déclaration de `str`.

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Si vous utilisez `auto` pour déclarer un pointeur de chaîne, le compilateur crée automatiquement la déclaration de type de pointeur `const` correcte. Une tentative de modification du contenu d'un pointeur `const` est signalée par le compilateur en tant qu'erreur.

> [!NOTE]
> La bibliothèque C++ Standard dans [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] ne prend pas en charge la **/Zc : strictstrings** builds de l’option du compilateur en mode débogage. Si vous voyez plusieurs [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) erreurs dans votre build de sortie, cela peut être la cause.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Modifier la **des Options supplémentaires** propriété à inclure **/Zc : strictstrings** , puis **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
