---
title: Erreur des outils Éditeur de liens LNK2019
ms.date: 12/15/2017
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.openlocfilehash: eb28ff3673c054b8ac1876d8ba736ceddfa5fd1a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449613"
---
# <a name="linker-tools-error-lnk2019"></a>Erreur des outils Éditeur de liens LNK2019

symbole externe non résolu '*symbole*'référencé dans la fonction'*fonction*'

Le code compilé pour *fonction* rend une référence ou un appel à *symbole*, mais ce symbole n’est pas défini dans les bibliothèques ou des fichiers objets spécifiés à l’éditeur de liens.

Ce message d’erreur est suivi d’une erreur irrécupérable [LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Vous devez corriger les erreurs de tous les LNK2001 et l’erreur LNK2019 pour corriger l’erreur LNK1120.

## <a name="possible-causes"></a>Causes possibles

Il existe plusieurs façons d’obtenir cette erreur, mais tous les impliquent une référence à une fonction ou une variable qui n’est pas de l’éditeur de liens *résoudre*, ou de trouver une définition pour. Le compilateur peut identifier quand un symbole n’est pas *déclaré*, mais pas quand il n’est pas *défini*, car la définition peut être dans un autre fichier source ou la bibliothèque. Si un symbole est appelé, mais jamais défini, l’éditeur de liens génère une erreur de symbole externe non résolu.

Voici un aperçu des problèmes courants qui provoquent l'erreur LNK2019 :

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-is-not-linked"></a>Le fichier objet ou la bibliothèque qui contient la définition du symbole n’est pas lié.

Dans Visual Studio, vérifiez que le fichier source qui contient la définition est créé et lié en tant que partie de votre projet. Sur la ligne de commande, vérifiez que le fichier source qui contient la définition est compilé, et que le fichier objet obtenu est inclus dans la liste des fichiers à lier.

### <a name="the-declaration-of-the-symbol-is-not-spelled-the-same-as-the-definition-of-the-symbol"></a>La déclaration du symbole n'est pas la même orthographe que la définition du symbole

Vérifiez l’orthographe et la casse est utilisé dans la déclaration et la définition et, là où le symbole est utilisé ou appelé.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-do-not-match-the-function-definition"></a>Une fonction est utilisée, mais le type ou le nombre de paramètres ne correspondent pas à la définition de fonction

La déclaration de la fonction doit correspondre à la définition. Vérifiez que l'appel de fonction correspond à la déclaration et que la déclaration correspond à la définition. Le code qui appelle des fonctions avec modèle doit aussi comporter des déclarations de fonctions avec modèle correspondantes qui incluent les mêmes paramètres de modèle que la définition. Pour obtenir un exemple d’une incompatibilité de déclaration de modèle, consultez l’exemple LNK2019e.cpp dans la section Exemples.

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Une fonction ou une variable est déclarée mais pas défini

Cela signifie généralement une déclaration existe dans un fichier d’en-tête, mais aucune définition correspondante n’est implémentée. Pour les fonctions membres ou les membres de données statiques, l'implémentation doit inclure le sélecteur de portée de classe. Pour obtenir un exemple, consultez [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>La convention d’appel est différente entre la déclaration de fonction et la définition de fonction

Les conventions d'appel ([__cdecl](../../cpp/cdecl.md), [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)ou [__vectorcall](../../cpp/vectorcall.md)) sont encodées dans le nom décoré. Vérifiez que la convention d'appel est identique.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-extern-c-in-a-c-file"></a>Un symbole est défini dans un fichier C, mais déclaré sans utiliser extern « C » dans un fichier C++

Les symboles définis dans un fichier compilé en C ont des noms décorés différents de ceux des symboles déclarés dans un fichier C++, sauf si vous utilisez un modificateur [extern "C"](../../cpp/using-extern-to-specify-linkage.md) . Vérifiez que la déclaration correspond à la liaison de compilation pour chaque symbole. De même, si vous définissez un symbole dans un fichier C++ qui sera utilisé par un programme C, utilisez `extern "C"` dans la définition.

### <a name="a-symbol-is-defined-as-static-and-then-later-referenced-outside-the-file"></a>Un symbole est défini comme étant static et par la suite référencé en dehors du fichier

En C++, contrairement à C, les [constantes globales](../../error-messages/tool-errors/global-constants-in-cpp.md) ont une liaison `static` . Pour contourner cette limitation, vous pouvez inclure les initialisations `const` dans un fichier d'en-tête et inclure cet en-tête dans vos fichiers .cpp. Vous pouvez aussi rendre la variable non constante et utiliser une référence constante pour y accéder.

### <a name="a-static-member-of-a-class-is-not-defined"></a>Un membre statique d’une classe n’est pas défini.

Un membre de classe statique doit avoir une définition unique. À défaut, il enfreint la règle de définition unique. Un membre de classe statique qui ne peut pas être défini comme étant inline doit être défini dans un fichier source à partir de son nom complet. S'il n'est pas du tout défini, l'éditeur de liens génère l'erreur LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Une dépendance de génération est définie uniquement comme une dépendance de projet dans la solution

Dans les versions antérieures de Visual Studio, ce niveau de dépendance était suffisant. Toutefois, à partir de Visual Studio 2010, Visual Studio requiert un [référence de projet à projet](/visualstudio/ide/managing-references-in-a-project). Si votre projet n'a pas de référence entre projets, il se peut que vous obteniez cette erreur de l'éditeur de liens. Ajoutez une référence entre projets pour corriger ce problème.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Vous générez une application console à l’aide des paramètres pour une application Windows

Si le message d’erreur est similaire à **symbole externe non résolu WinMain référencé dans la fonction** *function_name*, lien à l’aide de **/SUBSYSTEM : console** au lieu de **/SUBSYSTEM : Windows**. Pour plus d’informations sur ce paramètre et pour obtenir des instructions sur la façon de définir cette propriété dans Visual Studio, consultez [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Vous tentez de lier des bibliothèques de 64 bits à code 32 bits ou 32 bits des bibliothèques de code 64 bits

Bibliothèques et fichiers objet liés à votre code doivent être compilés pour la même architecture que votre code. Vérifiez que les bibliothèques de vos références de projet sont compilés pour la même architecture que votre projet. Assurez-vous que le [/LIBPATH](../../build/reference/libpath-additional-libpath.md) ou **répertoires de bibliothèques supplémentaires** option chemin d’accès utilisée par les points de l’éditeur de liens vers des bibliothèques pour l’architecture appropriée.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Vous utilisez différentes options de compilateur pour incorporer des fonctions inline dans différents fichiers sources

L’utilisation de fonctions inline définies dans des fichiers .cpp et le panachage d’options de compilateur pour incorporer des fonctions inline dans différents fichiers sources peut occasionner l’erreur LNK2019. Pour plus d'informations, consultez [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Vous utilisez des variables automatiques en dehors de leur étendue

Les variables automatiques (portée de fonction) ne peuvent être utilisées que dans la portée de la fonction en question. Ces variables ne peuvent pas être déclarées comme étant `extern` et utilisées dans d’autres fichiers sources. Pour obtenir un exemple, consultez [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-instrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-are-not-supported-on-your-target-architecture"></a>Vous appelez des fonctions intrinsèques ou passez des types d’arguments à des fonctions intrinsèques qui ne sont pas pris en charge dans votre architecture cible

Par exemple, si vous utilisez une fonction intrinsèque AVX2, mais que vous ne spécifiez pas l'option de compilateur [/ARCH:AVX2](../../build/reference/arch-x86.md) , le compilateur considère que la fonction intrinsèque est une fonction externe. Au lieu de générer une instruction inline, le compilateur génère un appel à un symbole externe avec le même nom que la fonction intrinsèque. Quand l'éditeur de liens tente de trouver la définition de cette fonction manquante, il génère l'erreur LNK2019. Vérifiez que vous utilisez uniquement des fonctions intrinsèques et des types pris en charge par votre architecture cible.

### <a name="you-mix-code-that-uses-native-wchart-with-code-that-doesnt"></a>Vous mélangez du code qui utilise wchar natif\_t avec le code qui ne fait pas

C++travail de la conformité du langage qui a été réalisé dans Visual Studio 2005 fait `wchar_t` un type natif par défaut. Vous devez utiliser le [/Zc :wchar_t-)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) option du compilateur à générer du code compatible avec les fichiers objets et de bibliothèque compilés à l’aide de versions antérieures de Visual Studio. Si tous les fichiers n’ont été compilés à l’aide de la même **/Zc:wchar\_t** paramètres, les références de type ne peut-être pas résolues en types compatibles. Vérifiez la compatibilité des types `wchar_t` dans tous les fichiers objets et de bibliothèque, soit en mettant à jour les types utilisés, soit en utilisant les mêmes paramètres **/Zc:wchar_t** au moment de la compilation.

## <a name="third-party-library-issues-and-vcpkg"></a>Problèmes de la bibliothèque tierce et Vcpkg

Si vous voyez cette erreur lorsque vous essayez de configurer une bibliothèque tierce dans le cadre de votre build, envisagez d’utiliser [Vcpkg](../../vcpkg.md), le Gestionnaire de Package Visual C++, à installer et générer la bibliothèque. Vcpkg prend en charge importante et croissante [liste des bibliothèques tierces](https://github.com/Microsoft/vcpkg/tree/master/ports)et définit toutes les propriétés de configuration et les dépendances requises pour les générations réussies dans le cadre de votre projet. Pour plus d’informations, consultez connexe [Blog Visual C++](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/) valider.

## <a name="diagnosis-tools"></a>Outils de diagnostic

Il peut être difficile de déterminer la raison qui empêche l'éditeur de liens de trouver une définition de symbole particulière. Souvent, le problème est que vous n’avez pas inclus le code qui contient la définition de votre build ou build options ont créé différents des noms de symboles externes décorés. Il existe plusieurs outils et options qui peuvent vous aider à diagnostiquer une erreur LNK2019.

- L'option d'éditeur de liens [/verbose](../../build/reference/verbose-print-progress-messages.md) peut vous aider à identifier les fichiers auxquels l'éditeur de liens fait référence. Cela peut vous aider à vérifier si le fichier qui contient la définition du symbole est inclus dans votre build.

- Le [/EXPORTE](../../build/reference/dash-exports.md) et [/symboles](../../build/reference/symbols.md) options de la **DUMPBIN** utilitaire peut vous aider à identifier les symboles sont définis dans vos fichiers .dll et objets ou bibliothèques. Vérifiez que les noms décorés exportés correspondent aux noms décorés que l'éditeur de liens recherche.

- Le **UNDNAME** utilitaire peut vous indiquer le symbole externe non décoré équivalent pour un nom décoré.

## <a name="examples"></a>Exemples

Voici plusieurs exemples de code qui génèrent une erreur LNK2019, ainsi que des informations permettant de corriger l'erreur.

### <a name="a-symbol-is-declared-but-not-defined"></a>Un symbole est déclaré mais pas défini

Dans cet exemple, une variable externe est déclarée mais pas définie :

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B is not available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Voici un autre exemple où une variable et une fonction sont déclarés comme `extern` mais aucune définition n’est fournie :

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

À moins que `i` et `g` sont définis dans un des fichiers inclus dans la build, l’éditeur de liens génère l’erreur LNK2019. Vous pouvez corriger les erreurs en incluant le fichier de code source qui contient les définitions dans le cadre de la compilation. Vous pouvez également transmettre les fichiers .obj ou .lib qui contiennent les définitions de l’éditeur de liens.

### <a name="a-static-data-member-is-declared-but-not-defined"></a>Un membre de données statique est déclaré mais pas défini

L'erreur LNK2019 peut aussi se produire quand un membre de données statique est déclaré mais pas défini. L'exemple suivant génère l'erreur LNK2019 et montre comment la corriger.

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

### <a name="declaration-parameters-do-not-match-definition"></a>Les paramètres de déclaration ne correspondent pas à la définition

Le code qui appelle des fonctions avec modèle doit comporter les déclarations de fonction avec modèle correspondantes. Les déclarations doivent inclure les mêmes paramètres de modèle que la définition. L'exemple suivant génère l'erreur LNK2019 sur un opérateur défini par l'utilisateur et montre comment la corriger.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration does not match the definition below:
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

### <a name="inconsistent-wchart-type-definitions"></a>Définitions de type wchar_t incohérentes

Cet exemple crée une DLL qui a une exportation qui utilise `WCHAR`, ce qui donne `wchar_t`.

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

L’exemple suivant utilise la DLL dans l’exemple précédent et génère l’erreur LNK2019, car les types non signés short * et WCHAR\* ne sont pas identiques.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Pour corriger cette erreur, modifiez `unsigned short` à `wchar_t` ou `WCHAR`, ou compilez LNK2019g.cpp en utilisant **/Zc :wchar_t-)** .

## <a name="additional-resources"></a>Ressources supplémentaires

Pour plus d’informations sur les causes et solutions pour LNK2001, consultez la question à Stack Overflow [qu’est une erreur de symbole externe non défini référence/non résolu et comment le corriger ?](https://stackoverflow.com/q/12573816/2002113).

