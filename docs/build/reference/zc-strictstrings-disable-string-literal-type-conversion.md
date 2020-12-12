---
description: 'En savoir plus sur : `/Zc:strictStrings` (désactiver la conversion de type de littéral de chaîne)'
title: /Zc:strictStrings (Désactiver la conversion du type de littéral de chaîne)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: 38c0ac2fe69acd81762fbf26797eece659ee63a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269053"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>`/Zc:strictStrings` (Désactiver la conversion de type de littéral de chaîne)

Lorsqu’il est spécifié, le compilateur requiert **`const`** une conformité stricte pour les pointeurs initialisés à l’aide de littéraux de chaîne.

## <a name="syntax"></a>Syntaxe

> **`/Zc:strictStrings`**[**`-`**]

## <a name="remarks"></a>Notes

Si **`/Zc:strictStrings`** est spécifié, le compilateur applique les qualifications C++ standard **`const`** pour les littéraux de chaîne, en tant que type « tableau de `const char` » ou « tableau de `const wchar_t` », en fonction de la déclaration. Les littéraux de chaîne sont immuables et une tentative de modification du contenu d'un de ces littéraux entraîne une erreur de violation d'accès au moment de l'exécution. Vous devez déclarer un pointeur de chaîne comme **`const`** pour l’initialiser à l’aide d’un littéral de chaîne ou utiliser un explicite **`const_cast`** pour initialiser un pointeur non- **`const`** . Par défaut, ou si **`/Zc:strictStrings-`** est spécifié, le compilateur n’applique pas les qualifications C++ standard **`const`** pour les pointeurs de chaîne initialisés à l’aide de littéraux de chaîne.

L' **`/Zc:strictStrings`** option est désactivée par défaut. L' [`/permissive-`](permissive-standards-conformance.md) option de compilateur définit implicitement cette option, mais elle peut être substituée à l’aide de **`/Zc:strictStrings-`** .

Utilisez l' **`/Zc:strictStrings`** option pour empêcher la compilation de code incorrect. Cet exemple montre comment une simple erreur de déclaration conduit à un incident au moment de l'exécution :

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

Lorsque **`/Zc:strictStrings`** est activé, le même code signale une erreur dans la déclaration de `str` .

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

Si vous utilisez **`auto`** pour déclarer un pointeur de chaîne, le compilateur crée la **`const`** déclaration de type de pointeur appropriée pour vous. Une tentative de modification du contenu d’un **`const`** pointeur est signalée par le compilateur comme une erreur.

> [!NOTE]
> La bibliothèque C++ standard dans Visual Studio 2013 ne prend pas en charge l' **`/Zc:strictStrings`** option de compilateur dans les versions Debug. Si vous voyez plusieurs erreurs de [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) dans la sortie de la génération, cela peut être dû à une erreur.

Pour plus d’informations sur les problèmes de conformité dans Visual C++, consultez [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **options supplémentaires** pour inclure **`/Zc:strictStrings`** , puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[`/Zc` Conformité](zc-conformance.md)<br/>
