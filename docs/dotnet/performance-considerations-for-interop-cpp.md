---
title: Considérations sur les performances de l'interopérabilité (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: c6b4456d9c75061c9a8c93f37f98b58f92adc899
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741847"
---
# <a name="performance-considerations-for-interop-c"></a>Considérations sur les performances de l'interopérabilité (C++)

Cette rubrique fournit des instructions pour réduire l’effet de transitions d’interopérabilité non managé sur les performances d’exécution.

Visual C++ prend en charge les mêmes mécanismes d’interopérabilité que d’autres langages .NET tels que Visual Basic et c# (P/Invoke), mais il fournit également la prise en charge de l’interopérabilité spécifique à Visual C++ (C++ interop). Pour les applications critiques pour les performances, il est important de comprendre les implications de performances de chaque technique d’interopérabilité.

Quelle que soit la technique d’interopérabilité utilisée, des séquences de transition spéciales, appelées thunks sont requis chaque fois qu’une fonction managée appelle une versa non managé de fonction et inversement. Ces thunks sont insérés automatiquement par le compilateur Visual C++, mais il est important de garder à l’esprit qu’ensemble, ces transitions peuvent être coûteuses en termes de performances.

## <a name="reducing-transitions"></a>Réduction des Transitions

Un pour éviter ou réduire le coût des thunks d’interopérabilité consiste à refactoriser les interfaces impliquées afin de réduire les transitions non managé. Améliore les performances permettre être réalisées en ciblant les interfaces bavardes, sont celles qui impliquent des appels fréquents entre la limite managée /. Une fonction managée qui appelle une fonction non managée dans une boucle serrée, est, par exemple, un bon candidat pour la refactorisation. Si la boucle elle-même est déplacée vers le côté non managé, ou si une alternative managée à l’appel non managé est créé (peut-être être des données de file d’attente sur le côté managé et ensuite le marshaling pour l’API non managée à la fois après la boucle), le nombre de transitions peut être réduite de connexion ificantly.

## <a name="pinvoke-vs-c-interop"></a>Visual Studio de P/Invoke. Interopérabilité C++

Pour les langages .NET, tels que Visual Basic et c#, la méthode recommandée pour l’interopérabilité avec les composants natifs est P/Invoke. Étant donné que P/Invoke est pris en charge par le .NET Framework, Visual C++ prend en charge également, mais Visual C++ fournit aussi sa propre prise en charge l’interopérabilité, qui est appelé interopérabilité C++. Interopérabilité C++ est préférable P/Invoke, car P/Invoke n’est pas un type sécurisé. Par conséquent, les erreurs sont principalement signalées au moment de l’exécution, mais interopérabilité C++ présente également les avantages de performances via P/Invoke.

Ces deux techniques nécessitent plusieurs choses se produire chaque fois qu’une fonction managée appelle une fonction non managée :

- Les arguments d’appel de fonction sont marshalés vers des types natifs du CLR.

- Un thunk non managés est exécuté.

- La fonction non managée est appelée (à l’aide de versions natives des arguments).

- Une conversion de code managé à managé est exécutée.

- Le type de retour et les « out » ou « dans, out » les arguments sont marshalés du code natif pour les types CLR.

Les thunks managés/non managés sont nécessaires pour l’interopérabilité fonctionne tout, mais le marshaling de données qui est nécessaire varie selon les types de données impliqués, la signature de fonction, et comment les données seront utilisées.

Le marshaling de données effectuées par l’interopérabilité C++ est la plus simple possible : les paramètres sont simplement copiés entre la limite managée/de manière au niveau du bit Aucune transformation n’est effectuée. Pour P/Invoke, cela vaut uniquement si tous les paramètres sont simples, des types blittables. Sinon, P/Invoke exécute une procédure très fiable pour convertir chaque paramètre managé en un type natif approprié, et vice versa si les arguments sont marqués comme « out », ou « dans, out ».

En d’autres termes, interopérabilité C++ utilise la méthode la plus rapide possible de marshaling de données, tandis que P/Invoke utilise la méthode la plus robuste. Cela signifie que l’interopérabilité C++ (dans une manière propre à C++) fournit des performances optimales par défaut, et que le programmeur est responsable de résoudre les cas où ce comportement n’est pas sûr ou approprié.

C’est pourquoi, interopérabilité C++ exige que le marshaling de données doit être fourni explicitement, mais l’avantage est que le programmeur est libre de décider ce qui est approprié, étant donné la nature des données, et comment il doit être utilisé. En outre, bien que le comportement de marshaling de données de P/Invoke peut être modifié et personnalisé dans une certaine mesure, interopérabilité C++ permet de personnaliser chaque appel par appel le marshaling de données. Cela n’est pas possible avec P/Invoke.

Pour plus d’informations sur l’interopérabilité C++, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)
