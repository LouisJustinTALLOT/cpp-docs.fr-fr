---
title: Erreur des outils Éditeur de liens LNK2019
description: À propos de l’éditeur de liens Microsoft Visual Studio erreur LNK2019 et comment le diagnostiquer et le corriger en code C et C++.
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- main
- WinMain
- wmain
- wWinMain
- __cdecl
- __stdcall
- __fastcall
- __vectorcall
- extern
- static
- const
- ARCH
- AVX2
- wchar_t
- VERBOSE
- EXPORTS
- SYMBOLS
- DUMPBIN
- UNDNAME
ms.openlocfilehash: d09e232b934761d138fee7324c462c915d919959
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509734"
---
# <a name="linker-tools-error-lnk2019"></a>Erreur des outils Éditeur de liens LNK2019

> externsymbole al non résolu'*symbol*'référencé dans la fonction'*Function*'

Le code compilé pour la *fonction* effectue une référence ou un appel au *symbole*, mais l’éditeur de liens ne peut pas trouver la définition du symbole dans les bibliothèques ou les fichiers objets à lier.

Ce message d’erreur est suivi de l’erreur irrécupérable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Pour corriger l’erreur LNK1120, vous devez d’abord corriger toutes les erreurs LNK2001 et LNK2019.

## <a name="possible-causes"></a>Causes possibles

Il existe de nombreuses façons d’effectuer cette erreur. Tous impliquent une référence à une fonction ou une variable que l’éditeur de liens n’a pas pu *résoudre*, ou trouver une définition pour. Le compilateur peut identifier le moment où un symbole n’est pas *déclaré*, mais il ne peut pas déterminer quand le symbole n’est pas *défini*. Cela est dû au fait que la définition peut se trouver dans un fichier source ou une bibliothèque différent (e). Si un symbole est référencé mais jamais défini, l’éditeur de liens génère une erreur de symbole al non résolue extern .

Voici un aperçu des problèmes courants qui provoquent l'erreur LNK2019 :

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>Le fichier source qui contient la définition du symbole n’est pas compilé

Dans Visual Studio, assurez-vous que le fichier source qui définit le symbole est compilé dans le cadre de votre projet. Vérifiez le répertoire de sortie de génération intermédiaire pour obtenir un fichier. obj correspondant. Si le fichier source n’est pas compilé, cliquez avec le bouton droit sur le fichier dans Explorateur de solutions, puis choisissez **Propriétés** pour vérifier les propriétés du fichier. La **Configuration Properties**  >  page**général** des propriétés de configuration doit afficher un **type d’élément** du **compilateur C/C++**. Sur la ligne de commande, assurez-vous que le fichier source qui contient la définition est compilé.

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>Le fichier objet ou la bibliothèque qui contient la définition du symbole n’est pas lié

Dans Visual Studio, assurez-vous que le fichier objet ou la bibliothèque qui contient la définition de symbole est lié dans le cadre de votre projet. Sur la ligne de commande, assurez-vous que la liste des fichiers à lier comprend le fichier objet ou la bibliothèque.

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>La déclaration du symbole n’est pas orthographiée de la même façon que la définition du symbole

Vérifiez que vous utilisez l’orthographe et la mise en majuscules correctes dans la déclaration et la définition, et quel que soit l’endroit où le symbole est utilisé ou appelé.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>Une fonction est utilisée, mais le type ou le nombre de paramètres ne correspond pas à la définition de fonction

La déclaration de la fonction doit correspondre à la définition. Assurez-vous que l’appel de fonction correspond à la déclaration et que la déclaration correspond à la définition. Le code qui appelle des fonctions avec modèle doit aussi comporter des déclarations de fonctions avec modèle correspondantes qui incluent les mêmes paramètres de modèle que la définition. Pour obtenir un exemple d’incompatibilité de déclaration de modèle, consultez l’exemple de LNK2019e. cpp dans la section exemples.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Une fonction ou une variable est déclarée, mais n’est pas définie

L’erreur LNK2019 peut se produire lorsqu’une déclaration existe dans un fichier d’en-tête, mais qu’aucune définition correspondante n’est implémentée. Pour les fonctions membres ou les static membres de données, l’implémentation doit inclure le sélecteur de portée de classe. Pour obtenir un exemple, consultez [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>La Convention d’appel est différente entre la déclaration de fonction et la définition de fonction

Les conventions d’appel ( [__cdecl](../../cpp/cdecl.md) , [__stdcall](../../cpp/stdcall.md) , [__fastcall](../../cpp/fastcall.md) ou [__vectorcall](../../cpp/vectorcall.md) ) sont encodées dans le cadre du nom décoré. Assurez-vous que la Convention d’appel est la même.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>Un symbole est défini dans un fichier C, mais déclaré sans utiliser extern "C" dans un fichier C++

Les symboles définis dans un fichier compilé en C ont des noms décorés différents des symboles déclarés dans un fichier C++, sauf si vous utilisez un modificateur [ extern « C »](../../cpp/extern-cpp.md) . Assurez-vous que la déclaration correspond à la liaison de compilation pour chaque symbole. De même, si vous définissez un symbole dans un fichier C++ qui sera utilisé par un programme C, utilisez `extern "C"` dans la définition.

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>Un symbole est défini comme static , puis référencé ultérieurement en dehors du fichier

En C++, contrairement à C, les [ const ants globaux](../../error-messages/tool-errors/global-constants-in-cpp.md) ont une **`static`** liaison. Pour contourner cette limitation, vous pouvez inclure les **`const`** initialisations dans un fichier d’en-tête et inclure cet en-tête dans vos fichiers. cpp, ou vous pouvez faire en sorte que la variable ne soit pas const ant et utilise une const référence ant pour y accéder.

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>Un static membre d’une classe n’est pas défini

Un static membre de classe doit avoir une définition unique, ou il violera la règle à une seule définition. Un static membre de classe qui ne peut pas être défini inline doit être défini dans un fichier source à l’aide de son nom complet. S’il n’est pas défini, l’éditeur de liens génère l’erreur LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Une dépendance de génération est définie uniquement comme une dépendance de projet dans la solution

Dans les versions antérieures de Visual Studio, ce niveau de dépendance était suffisant. Toutefois, à compter de Visual Studio 2010, Visual Studio requiert une [référence](/visualstudio/ide/managing-references-in-a-project)entre projets. Si votre projet n’a pas de référence entre projets, vous pouvez recevoir cette erreur de l’éditeur de liens. Ajoutez une référence entre projets pour corriger ce problème.

### <a name="an-entry-point-isnt-defined"></a>Un point d’entrée n’est pas défini

Le code d’application doit définir un point d’entrée approprié : `main` ou `wmain` pour les applications console, et `WinMain` ou `wWinMain` pour les applications Windows. Pour plus d’informations, consultez [ main fonctions et arguments de ligne de commande](../../cpp/main-function-command-line-args.md) ou fonction. [ WinMain ](/windows/win32/api/winbase/nf-winbase-winmain) Pour utiliser un point d’entrée personnalisé, spécifiez l’option de l’éditeur de liens [/entry (symbole de point d’entrée)](../../build/reference/entry-entry-point-symbol.md) .

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Vous générez une application console en utilisant les paramètres d’une application Windows

Si le message d’erreur est semblable **au extern symbole al non résolu WinMain référencé dans la fonction** *function_name*, liez-le à l’aide de **/SUBSYSTEM : console** au lieu de **/SUBSYSTEM : Windows**. Pour plus d’informations sur ce paramètre et pour obtenir des instructions sur la façon de définir cette propriété dans Visual Studio, consultez [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Vous tentez de lier des bibliothèques 64 bits au code 32 bits, ou des bibliothèques 32 bits au code 64 bits

Les bibliothèques et les fichiers objets liés à votre code doivent être compilés pour la même architecture que votre code. Assurez-vous que les bibliothèques que vos références de projet sont compilées pour la même architecture que votre projet. Assurez-vous que la propriété [/LIBPATH](../../build/reference/libpath-additional-libpath.md) ou **répertoires de bibliothèques supplémentaires** pointe vers les bibliothèques générées pour l’architecture correcte.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Vous utilisez différentes options de compilateur pour incorporer des fonctions dans différents fichiers sources

L’utilisation de fonctions inline définies dans des fichiers .cpp et le panachage d’options de compilateur pour incorporer des fonctions inline dans différents fichiers sources peut occasionner l’erreur LNK2019. Pour plus d'informations, consultez [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Vous utilisez des variables automatiques en dehors de leur portée

Les variables automatiques (portée de fonction) ne peuvent être utilisées que dans la portée de la fonction en question. Ces variables ne peuvent pas être déclarées **`extern`** et utilisées dans d’autres fichiers sources. Pour obtenir un exemple, consultez [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>Vous appelez des fonctions intrinsèques ou transmettez des types d’arguments à des fonctions intrinsèques qui ne sont pas prises en charge sur votre architecture cible

Par exemple, si vous utilisez un AVX2 intrinsèque, mais que vous ne spécifiez pas l’option [ / ARCH : AVX2 ](../../build/reference/arch-x86.md) du compilateur, le compilateur suppose que l’intrinsèque est une extern fonction al. Au lieu de générer une instruction Inline, le compilateur génère un appel à un extern symbole al portant le même nom que le intrinsèque. Quand l'éditeur de liens tente de trouver la définition de cette fonction manquante, il génère l'erreur LNK2019. Veillez à utiliser uniquement des fonctions intrinsèques et des types pris en charge par votre architecture cible.

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>Vous mélangez du code qui utilise native wchar_t avec du code qui ne

Le travail de mise en conformité du langage C++ effectué dans Visual Studio 2005 a rendu **`wchar_t`** un type natif par défaut. Si tous les fichiers n’ont pas été compilés à l’aide du même **/Zc : wchar_t ** Settings, les références de type risquent de ne pas être résolues en types compatibles. Assurez-vous que **`wchar_t`** les types dans tous les fichiers objets et de bibliothèque sont compatibles. Effectuez une mise à jour à partir d’un **`wchar_t`** typedef ou utilisez des paramètres **/Zc wchar_t :** Settings cohérents quand vous compilez.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de bibliothèque tierce et vcpkg

Si vous voyez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre Build, envisagez d’utiliser [vcpkg](../../build/vcpkg.md), un gestionnaire de package C++, pour installer et générer la bibliothèque. vcpkg prend en charge une liste importante et croissante [de bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports). Il définit toutes les propriétés de configuration et les dépendances requises pour les builds réussies dans le cadre de votre projet.

## <a name="diagnosis-tools"></a>Outils de diagnostic

Il est parfois difficile de savoir pourquoi l’éditeur de liens ne peut pas trouver une définition de symbole particulière. Souvent, le problème est que vous n’avez pas inclus le code qui contient la définition dans votre Build. Ou, les options de génération ont créé des noms décorés différents pour les extern symboles al. Il existe plusieurs outils et options qui peuvent vous aider à diagnostiquer les erreurs LNK2019.

- L' [/VERBOSE](../../build/reference/verbose-print-progress-messages.md) option de l’éditeur de liens peut vous aider à déterminer les fichiers auxquels l’éditeur de liens fait référence. Cette option peut vous aider à vérifier si le fichier qui contient la définition du symbole est inclus dans votre Build.

- Les [/EXPORTS](../../build/reference/dash-exports.md) [/SYMBOLS](../../build/reference/symbols.md) options et de l' **DUMPBIN** utilitaire peuvent vous aider à identifier les symboles qui sont définis dans vos fichiers. dll et objets ou bibliothèques. Assurez-vous que les noms décorés exportés correspondent aux noms décorés que l’éditeur de liens recherche.

- L' **UNDNAME** utilitaire peut vous indiquer le symbole al non décoré équivalent extern pour un nom décoré.

## <a name="examples"></a>Exemples

Voici plusieurs exemples de code qui génèrent une erreur LNK2019, ainsi que des informations permettant de corriger l'erreur.

### <a name="a-symbol-is-declared-but-not-defined"></a>Un symbole est déclaré mais pas défini

Dans cet exemple, une extern variable Al est déclarée, mais pas définie :

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Voici un autre exemple dans lequel une variable et une fonction sont déclarées, **`extern`** mais aucune définition n’est fournie :

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

À moins que `i` et `g` ne soient définis dans l’un des fichiers inclus dans la build, l’éditeur de liens génère l’erreur LNK2019. Vous pouvez corriger les erreurs en incluant le fichier de code source qui contient les définitions dans le cadre de la compilation. Vous pouvez également passer des fichiers. obj ou. lib qui contiennent les définitions à l’éditeur de liens.

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>Un static membre de données est déclaré mais pas défini

L’erreur LNK2019 peut également se produire quand un static membre de données est déclaré mais pas défini. L'exemple suivant génère l'erreur LNK2019 et montre comment la corriger.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-dont-match-the-definition"></a>Les paramètres de déclaration ne correspondent pas à la définition

Le code qui appelle des fonctions avec modèle doit comporter les déclarations de fonction avec modèle correspondantes. Les déclarations doivent inclure les mêmes paramètres de modèle que la définition. L'exemple suivant génère l'erreur LNK2019 sur un opérateur défini par l'utilisateur et montre comment la corriger.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>Définitions de types incohérents wchar_t

Cet exemple crée une DLL qui a une exportation qui utilise `WCHAR` , qui correspond à **`wchar_t`** .

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

L’exemple suivant utilise la DLL de l’exemple précédent et génère l’erreur LNK2019, car les types `unsigned short*` et `WCHAR*` ne sont pas identiques.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Pour corriger cette erreur, remplacez **`unsigned short`** par **`wchar_t`** ou `WCHAR` , ou compilez LNK2019g. cpp en utilisant **/Zc : wchar_t - **.

## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations sur les causes et solutions possibles pour LNK2001, consultez la Stack Overflow question [qu’est-ce qu’une erreur de symbole al non défini/non définie extern et comment la corriger ?](https://stackoverflow.com/q/12573816/2002113).
