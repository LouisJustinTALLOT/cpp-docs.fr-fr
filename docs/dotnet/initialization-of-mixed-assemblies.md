---
title: Initialisation d'assemblys mixtes
ms.date: 03/09/2018
helpviewer_keywords:
- mixed assemblies [C++], loader lock
- loader lock [C++]
- initializing mixed assemblies
- deadlocks [C++]
- .cctor [C++]
- custom locales [C++]
- mixed assemblies [C++], initilizing
ms.assetid: bfab7d9e-f323-4404-bcb8-712b15f831eb
ms.openlocfilehash: 35dd47bd87c278d60fc616dca854bf843acc7c57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "70311916"
---
# <a name="initialization-of-mixed-assemblies"></a>Initialisation d'assemblys mixtes

Les développeurs Windows doivent toujours faire attention au verrouillage du chargeur lors de l' `DllMain`exécution du code pendant. Toutefois, il existe des problèmes supplémentaires à prendre en compte lors du C++traitement des assemblys en mode mixte/CLR.

Le code dans [DllMain](/windows/win32/Dlls/dllmain) ne doit pas accéder au CLR (Common Language Runtime) .net. Cela signifie que `DllMain` ne doit pas appeler de fonctions managées, directement ou indirectement ; aucun code managé ne doit être déclaré ou `DllMain`implémenté dans ; et aucun garbage collection ou chargement de bibliothèque automatique ne `DllMain` doit avoir lieu dans .

## <a name="causes-of-loader-lock"></a>Causes du verrouillage du chargeur

Avec l’introduction de la plateforme .NET, il existe deux mécanismes distincts pour charger un module d’exécution (EXE ou DLL) : un pour Windows, qui est utilisé pour les modules non managés et un pour le CLR, qui charge les assemblys .NET. Le problème du chargement de DLL mixtes se concentre autour du chargeur du système d’exploitation Microsoft Windows.

Quand un assembly qui contient uniquement des constructions .NET est chargé dans un processus, le chargeur du CLR peut exécuter toutes les tâches de chargement et d’initialisation nécessaires lui-même. Toutefois, dans la mesure où les assemblys mixtes peuvent contenir du code natif et des données, le chargeur Windows doit aussi être utilisé.

Le chargeur Windows garantit qu’aucun code ne peut accéder au code ou aux données de cette DLL avant qu’elle n’ait été initialisée, et qu’aucun code ne peut charger la DLL de façon redondante pendant qu’elle est partiellement initialisée. Pour ce faire, le chargeur Windows utilise une section critique de processus global (souvent appelée « verrouillage du chargeur ») qui empêche l’accès non sécurisé pendant l’initialisation du module. Le processus de chargement est donc vulnérable pour de nombreux scénarios d’interblocage classiques. Pour les assemblys mixtes, les deux scénarios suivants augmentent le risque d’interblocage :

- Tout d’abord, si les utilisateurs tentent d’exécuter des fonctions compilées en langage MSIL (Microsoft Intermediate Language) quand le verrouillage `DllMain` du chargeur est maintenu (à partir de ou dans les initialiseurs statiques, par exemple), il peut provoquer un interblocage. Considérez le cas dans lequel la fonction MSIL fait référence à un type dans un assembly qui n’a pas été chargé. Le CLR tente de charger automatiquement cet assembly, ce qui peut nécessiter le blocage du chargeur Windows sur le verrouillage du chargeur. Un blocage se produit, car le verrou du chargeur est déjà détenu par du code précédemment dans la séquence d’appel. Toutefois, l’exécution du langage MSIL pendant le verrouillage du chargeur ne garantit pas qu’un blocage se produira, ce qui rendra ce scénario difficile à diagnostiquer et à résoudre. Dans certains cas, par exemple quand la DLL du type référencé ne contient pas de constructions natives et que toutes ses dépendances ne contiennent pas de constructions natives, le chargeur Windows n’est pas obligé de charger l’assembly .NET du type référencé. En outre, l’assembly exigé ou ses dépendances natives/.NET mixtes ont peut-être déjà été chargés par un autre code. L’interblocage peut donc être difficile à prédire et peut varier selon la configuration de l’ordinateur cible.

- Deuxièmement, lors du chargement de dll dans les versions 1,0 et 1,1 du .NET Framework, le CLR supposait que le verrouillage du chargeur n’était pas maintenu et exécutait plusieurs actions qui ne sont pas valides lors du verrouillage du chargeur. En supposant que le verrouillage du chargeur n’est pas détenu est une hypothèse valide pour les dll purement .NET, mais, comme les dll mixtes exécutent des routines d’initialisation natives, elles nécessitent le chargeur Windows natif et, par conséquent, le verrou du chargeur. Ainsi, même si le développeur n’essayait pas d’exécuter des fonctions MSIL pendant l’initialisation des DLL, il persistait un faible risque d’interblocage non déterministe avec les versions 1.0 et 1.1 du .NET Framework.

Le non-déterminisme a été entièrement supprimé du processus de chargement de DLL mixtes Il a été accompli avec les modifications suivantes :

- Le CLR ne fait plus de fausses hypothèses lors du chargement de DLL mixtes.

- L’initialisation non managée et managée est exécutée en deux étapes distinctes. L’initialisation non managée a lieu en premier (par le biais de DllMain), et l’initialisation managée a lieu après, à l’aide d’un. Construction prise en `.cctor` charge par .net. Cette dernière opération est complètement transparente pour l’utilisateur, sauf si **/Zl** ou **/NODEFAULTLIB** est utilisé. Pour plus d’informations, consultez[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md) et [/Zl (Omit Default Library Name)](../build/reference/zl-omit-default-library-name.md) .

Le verrouillage du chargeur peut encore se produire, mais il est désormais détecté et se produit de façon déterministe. Si `DllMain` contient des instructions MSIL, le compilateur génère un avertissement [du compilateur d’avertissement (niveau 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md). En outre, le CRT ou le CLR tente de détecter et de signaler les tentatives d’exécution du MSIL pendant le verrouillage du chargeur. La détection du CRT se traduit par le diagnostic du runtime C Run-Time Error R6033.

Le reste de ce document décrit les autres scénarios dans lesquels des instructions MSIL peuvent s’exécuter pendant le verrouillage du chargeur, les solutions au problème dans chacun de ces scénarios et les techniques de débogage.

## <a name="scenarios-and-workarounds"></a>Scénarios et solutions de contournement

Dans plusieurs cas de figure, le code utilisateur peut exécuter des instructions MSIL pendant le verrouillage du chargeur. Le développeur doit s’assurer que l’implémentation du code utilisateur ne tente pas d’exécuter des instructions MSIL dans chacune de ces circonstances. Les sous-sections suivantes décrivent toutes les possibilités tout en indiquant comment résoudre les problèmes dans les cas les plus courants.

### <a name="dllmain"></a>DllMain

La `DllMain` fonction est un point d’entrée défini par l’utilisateur pour une dll. Sauf indication contraire de l’utilisateur, la fonction `DllMain` est appelée chaque fois qu’un processus ou un thread s’attache à la DLL conteneur ou s’en détache. Dans la mesure où cet appel peut se produire alors que le verrouillage du chargeur est maintenu, aucune fonction `DllMain` fournie par l’utilisateur ne doit être compilée en langage MSIL. En outre, aucune fonction dans l’arborescence des appels associée à une racine `DllMain` ne peut être compilée en langage MSIL. Pour résoudre les problèmes à cet emplacement, le bloc de code qui définit `DllMain` doit être modifié avec #pragma `unmanaged`. Il en va de même pour chaque fonction que `DllMain` appelle.

Dans les cas où ces fonctions doivent appeler une fonction qui nécessite une implémentation MSIL pour d’autres contextes appelants, une stratégie de duplication peut être utilisée quand une version .NET et une version native de la même fonction sont créées.

Sinon, si `DllMain` n’est pas nécessaire ou qu’il est inutile de l’exécuter pendant le verrouillage du chargeur, l’implémentation de `DllMain` fournie par l’utilisateur peut être supprimée, ce qui élimine le problème.

Si DllMain tente d’exécuter des instructions MSIL directement, vous obtenez l’avertissement suivant : [Compiler Warning (level 1) C4747](../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md) . Toutefois, le compilateur ne peut pas détecter les cas où DllMain appelle une fonction dans un autre module qui, à son tour, tente d’exécuter des instructions MSIL.

Pour plus d’informations sur ce scénario, consultez [obstacles au diagnostic](#impediments-to-diagnosis).

### <a name="initializing-static-objects"></a>Initialisation d'objets statiques

L’initialisation d’objets statiques peut entraîner un interblocage si un initialiseur dynamique est exigé. Pour les cas simples, par exemple quand une variable statique est assignée à une valeur connue au moment de la compilation, aucune initialisation dynamique n’est requise, donc il n’y a aucun risque d’interblocage. Toutefois, les variables statiques initialisées par les appels de fonction, les appels de constructeur ou les expressions qui ne peuvent pas être évaluées au moment de la compilation exigent tous une exécution de code pendant l’initialisation de module.

Le code suivant montre des exemples d’initialiseurs statiques qui exigent une initialisation dynamique : un appel de fonction, une construction d’objet et une initialisation de pointeur. (Ces exemples ne sont pas statiques, mais sont supposés tels qu’ils sont définis dans la portée globale, ce qui a le même effet.)

```cpp
// dynamic initializer function generated
int a = init();
CObject o(arg1, arg2);
CObject* op = new CObject(arg1, arg2);
```

Ce risque d’interblocage varie selon que le module conteneur est compilé avec **/clr** et que les instructions MSIL sont exécutées. Plus particulièrement, si la variable statique est compilée sans **/clr** (ou réside dans un bloc #pragma `unmanaged` ) et que l’initialiseur dynamique nécessaire pour l’initialiser entraîne l’exécution d’instructions MSIL, un interblocage peut se produire. Cela est dû au fait que, pour les modules compilés sans **/CLR**, l’initialisation des variables statiques est effectuée par DllMain. En revanche, les variables statiques compilées avec **/CLR** sont initialisées par le `.cctor`, une fois l’étape d’initialisation non managée terminée et le verrouillage du chargeur libéré.

Il existe de nombreuses méthodes permettant de résoudre l’interblocage provoqué par l’initialisation dynamique de variables statiques (classées globalement selon le délai nécessaire pour résoudre le problème) :

- Le fichier source contenant la variable statique peut être compilé avec **/clr**.

- Toutes les fonctions appelées par la variable statique peuvent être compilées en code natif à l’aide de la directive #pragma `unmanaged` .

- Clonez manuellement le code dont dépend la variable statique, en fournissant à la fois une version .NET et une version native avec des noms différents. Les développeurs peuvent ensuite appeler la version native à partir d’initialiseurs statiques natifs et appeler la version .NET ailleurs.

### <a name="user-supplied-functions-affecting-startup"></a>Fonctions fournies par l’utilisateur affectant le démarrage

Il existe plusieurs fonctions fournies par l’utilisateur dont dépendent les bibliothèques pour l’initialisation au démarrage. Par exemple, lors de la surcharge globale d’opérateurs dans C++ , tels que `new` les `delete` opérateurs et, les versions fournies par l’utilisateur sont utilisées partout, C++ y compris dans l’initialisation et la destruction de la bibliothèque standard. Par conséquent, C++ la bibliothèque standard et les initialiseurs statiques fournis par l’utilisateur appellera les versions fournies par l’utilisateur de ces opérateurs.

Si les versions fournies par l’utilisateur sont compilées en langage MSIL, ces initialiseurs tentent alors d’exécuter des instructions MSIL pendant que le verrouillage du chargeur est maintenu. Un fourni `malloc` par l’utilisateur a les mêmes conséquences. Pour résoudre ce problème, n’importe laquelle de ces surcharges ou définitions fournies par l’utilisateur doit être implémentée sous la forme de code natif à l’aide de la directive #pragma `unmanaged` .

Pour plus d’informations sur ce scénario, consultez [obstacles au diagnostic](#impediments-to-diagnosis).

### <a name="custom-locales"></a>Paramètres régionaux personnalisés

Si l’utilisateur fournit des paramètres régionaux globaux personnalisés, ces paramètres régionaux sont utilisés pour initialiser tous les futurs flux d’e/s, y compris les flux qui sont initialisés de manière statique. Si cet objet de paramètres régionaux globaux est compilé en langage MSIL, les fonctions membres d’objets de paramètres régionaux compilées en langage MSIL peuvent être appelées pendant que le verrouillage du chargeur est maintenu.

Il existe trois options pour résoudre ce problème :

Les fichiers sources contenant toutes les définitions de flux d’E/S globales peuvent être compilés à l’aide de l’option **/clr** , Elle empêche l’exécution de leurs initialiseurs statiques pendant le verrouillage du chargeur.

Les définitions de fonctions personnalisées de paramètres régionaux peuvent être compilées en code natif en utilisant la directive #pragma `unmanaged` .

Abstenez-vous de définir les paramètres régionaux personnalisés comme paramètres régionaux globaux tant que le verrouillage du chargeur n’a pas été désactivé. Configurez ensuite de façon explicite les flux d’E/S créés pendant l’initialisation avec les paramètres régionaux personnalisés.

## <a name="impediments-to-diagnosis"></a>Obstacles au diagnostic

Dans certains cas, il est difficile de détecter la source des blocages. Les sous-sections suivantes présentent ces scénarios et la façon de contourner ces problèmes.

### <a name="implementation-in-headers"></a>Implémentation dans les en-têtes

Dans des cas spécifiques, les implémentations de fonctions à l’intérieur des fichiers d’en-tête peuvent compliquer le diagnostic. Les fonctions inline et le code du modèle exigent que les fonctions soient spécifiées dans un fichier d’en-tête.  Le langage C++ spécifie la règle de définition unique, qui force toutes les implémentations de fonctions ayant le même nom à être sémantiquement équivalentes. L’éditeur de liens C++ n’a pas besoin de faire de considérations spéciales quand il fusionne des fichiers objets qui ont des implémentations en double d’une fonction donnée.

Avant Visual Studio 2005, l’éditeur de liens choisit simplement la plus grande de ces définitions sémantiquement équivalentes, pour tenir compte des déclarations anticipées et des scénarios quand différentes options d’optimisation sont utilisées pour des fichiers sources différents. Il crée un problème pour les DLL natives/.net mixtes.

Étant donné que le même en-tête peut C++ être inclus à la fois par les fichiers avec **/CLR** activé et désactivé, ou `#pragma unmanaged` un #include peut être encapsulé dans un bloc, il est possible d’avoir des versions MSIL et natives des fonctions qui fournissent des implémentations dans en-têtes. Les implémentations MSIL et natives ont des sémantiques différentes en ce qui concerne l’initialisation pendant le verrouillage du chargeur, ce qui viole en pratique la règle de définition unique. Quand l’éditeur de liens choisit l’implémentation la plus importante, il peut donc choisir la version MSIL d’une fonction, même si elle a été compilée explicitement ailleurs en code natif à l’aide de la directive #pragma unmanaged. Pour garantir qu’une version MSIL d’un modèle ou d’une fonction inline n’est jamais appelée pendant le verrouillage du chargeur, chaque définition de chaque fonction de ce type appelée sous verrouillage du `#pragma unmanaged` chargeur doit être modifiée à l’aide de la directive. Si le fichier d’en-tête provient d’un tiers, le moyen le plus simple d’effectuer cette modification consiste à `#pragma unmanaged` envoyer et à dépiler la directive autour de la directive #include pour le fichier d’en-tête incriminé. (Pour obtenir un exemple [, consultez managé, non managé](../preprocessor/managed-unmanaged.md) .) Toutefois, cette stratégie ne fonctionne pas pour les en-têtes qui contiennent un autre code qui doit appeler directement des API .NET.

À titre de commodité pour les utilisateurs confrontés au verrouillage du chargeur, l’éditeur de liens choisit l’implémentation native par rapport à l’implémentation managée en cas de présentation des deux implémentations. Cette valeur par défaut évite les problèmes ci-dessus. Toutefois, il y a deux exceptions à cette règle dans cette version en raison de deux problèmes non résolus avec le compilateur :

- L’appel à une fonction Inline s’effectue via un pointeur de fonction statique globale. Ce scénario est notable, car les fonctions virtuelles sont appelées par le biais de pointeurs de fonction globale. Par exemple,

```cpp
#include "definesmyObject.h"
#include "definesclassC.h"

typedef void (*function_pointer_t)();

function_pointer_t myObject_p = &myObject;

#pragma unmanaged
void DuringLoaderlock(C & c)
{
    // Either of these calls could resolve to a managed implementation,
    // at link-time, even if a native implementation also exists.
    c.VirtualMember();
    myObject_p();
}
```

### <a name="diagnosing-in-debug-mode"></a>Diagnostic en mode débogage

Toutes les opérations de diagnostic des problèmes liés au verrouillage du chargeur doivent être effectuées sur des builds Debug. Les builds Release ne peuvent pas produire de diagnostic et les optimisations réalisées en mode Release peuvent masquer une partie du langage MSIL dans les scénarios de verrouillage du chargeur.

## <a name="how-to-debug-loader-lock-issues"></a>Comment déboguer les problèmes de verrouillage du chargeur

Le diagnostic que le CLR génère quand une fonction MSIL est appelée provoque l’interruption de l’exécution du CLR. À son tour, le débogueur en mode mixte visuel C++ est également suspendu lors de l’exécution de l’élément débogué in-process. Toutefois, lors de l’attachement au processus, il n’est pas possible d’obtenir une pile des appels managée pour le programme débogué à l’aide du débogueur mixte.

Pour identifier la fonction MSIL spécifique qui a été appelée pendant le verrouillage du chargeur, les développeurs doivent effectuer les étapes suivantes :

1. Vérifiez que les symboles de mscoree.dll et mscorwks.dll sont disponibles.

   Vous pouvez rendre les symboles disponibles de deux manières. Premièrement, les fichiers PDB de mscoree.dll et mscorwks.dll peuvent être ajoutés au chemin de recherche de symboles. Pour les ajouter, ouvrez la boîte de dialogue Options du chemin de recherche de symboles. (Dans le menu **Outils** , choisissez **options**. Dans le volet gauche de la boîte de dialogue **options** , ouvrez le nœud **débogage** , puis choisissez **symboles**.) Ajoutez le chemin aux fichiers PDB de mscoree.dll et mscorwks.dll à la liste de recherche. Ces PDB sont installés dans %VSINSTALLDIR%\SDK\v2.0\symbols. Cliquez sur **OK**.

   Deuxièmement, les fichiers PDB de mscoree.dll et mscorwks.dll peuvent être téléchargés à partir du serveur de symboles Microsoft. Pour configurer le serveur de symboles, ouvrez la boîte de dialogue des options du chemin de recherche de symboles. (Dans le menu **Outils** , choisissez **options**. Dans le volet gauche de la boîte de dialogue **options** , ouvrez le nœud **débogage** , puis choisissez **symboles**.) Ajoutez ce chemin de recherche à la liste de `https://msdl.microsoft.com/download/symbols`recherche :. Ajoutez un répertoire de cache de symboles à la zone de texte du cache du serveur de symboles. Cliquez sur **OK**.

1. Définissez le mode du débogueur en mode natif uniquement.

   Ouvrez la grille **Propriétés** du projet de démarrage dans la solution. Sélectionnez **Configuration Propriétés** > **débogage**. Affectez au **type de débogueur** la valeur **natif uniquement**.

1. Démarrez le débogueur (F5).

1. Quand le diagnostic **/CLR** est généré, choisissez **Réessayer** , puis **arrêter**.

1. Ouvrez la fenêtre Pile des appels. (Dans la barre de menus, **Choisissez déboguer** > la**pile des appels** **Windows** > .) L’initialiseur `DllMain` incriminé ou statique est identifié par une flèche verte. Si la fonction incriminée n’est pas identifiée, vous devez effectuer les étapes suivantes pour la rechercher.

1. Ouvrez la **fenêtre exécution** (dans la barre de menus, **Choisissez déboguer** > les**fenêtres** > **immédiates**.)

1. Entrez `.load sos.dll` dans la fenêtre **exécution** pour charger le service de débogage SOS.

1. Entrez `!dumpstack` dans la fenêtre **exécution** pour obtenir une liste complète de la pile **/CLR** interne.

1. Recherchez la première instance (la plus proche du bas de la pile) de _ cordllmain (si `DllMain` provoque le problème) ou _VTableBootstrapThunkInitHelperStub ou GetTargetForVTableEntry (si un initialiseur statique est à l’origine du problème). L’entrée de la pile juste en dessous de cet appel est l’appel de la fonction MSIL implémentée qui a tenté de s’exécuter pendant le verrouillage du chargeur.

1. Accédez au fichier source et au numéro de ligne identifiés à l’étape précédente, puis corrigez le problème à l’aide des scénarios et des solutions décrits dans la section scénarios.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre comment éviter le verrouillage du chargeur en déplaçant le `DllMain` code de dans le constructeur d’un objet global.

Dans cet exemple, il existe un objet managé global dont le constructeur contient l’objet managé qui se trouvait à `DllMain`l’origine. La deuxième partie de cet exemple référence l’assembly, en créant une instance de l’objet managé pour appeler le constructeur de module qui effectue l’initialisation.

### <a name="code"></a>Code

```cpp
// initializing_mixed_assemblies.cpp
// compile with: /clr /LD
#pragma once
#include <stdio.h>
#include <windows.h>
struct __declspec(dllexport) A {
   A() {
      System::Console::WriteLine("Module ctor initializing based on global instance of class.\n");
   }

   void Test() {
      printf_s("Test called so linker does not throw away unused object.\n");
   }
};

#pragma unmanaged
// Global instance of object
A obj;

extern "C"
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved) {
   // Remove all managed code from here and put it in constructor of A.
   return true;
}
```

Cet exemple illustre des problèmes d’initialisation d’assemblys mixtes :

```cpp
// initializing_mixed_assemblies_2.cpp
// compile with: /clr initializing_mixed_assemblies.lib
#include <windows.h>
using namespace System;
#include <stdio.h>
#using "initializing_mixed_assemblies.dll"
struct __declspec(dllimport) A {
   void Test();
};

int main() {
   A obj;
   obj.Test();
}
```

Ce code génère la sortie suivante :

```Output
Module ctor initializing based on global instance of class.

Test called so linker does not throw away unused object.
```

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
