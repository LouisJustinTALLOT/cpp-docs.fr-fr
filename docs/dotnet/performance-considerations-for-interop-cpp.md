---
description: 'En savoir plus sur : considérations relatives aux performances pour l’interopérabilité (C++)'
title: Considérations sur les performances de l'interopérabilité (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
ms.openlocfilehash: 29723f0ea5c7b745100ab4c7abb7f59abce47db6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255558"
---
# <a name="performance-considerations-for-interop-c"></a>Considérations sur les performances de l'interopérabilité (C++)

Cette rubrique fournit des instructions pour réduire l’effet des transitions d’interopérabilité managées/non managées sur les performances d’exécution.

Visual C++ prend en charge les mêmes mécanismes d’interopérabilité que d’autres langages .NET tels que Visual Basic et C# (P/Invoke), mais il fournit également une prise en charge de l’interopérabilité qui est spécifique à Visual C++ (interopérabilité C++). Pour les applications critiques pour les performances, il est important de comprendre les implications en matière de performances de chaque technique d’interopérabilité.

Quelle que soit la technique d’interopérabilité utilisée, les séquences de transition spéciales, appelées thunks, sont nécessaires chaque fois qu’une fonction managée appelle une fonction non managée, et vice versa. Ces thunks sont insérés automatiquement par le compilateur Microsoft C++, mais il est important de garder à l’esprit que ces transitions peuvent être coûteuses en termes de performances.

## <a name="reducing-transitions"></a>Réduction des transitions

Une façon d’éviter ou de réduire le coût des thunks d’interopérabilité consiste à refactoriser les interfaces impliquées pour réduire les transitions managées/non managées. Des améliorations considérables en matière de performances peuvent être apportées en ciblant les interfaces bavardes, c’est-à-dire celles qui impliquaient des appels fréquents à travers la limite gérée/non gérée. Une fonction managée qui appelle une fonction non managée dans une boucle serrée, par exemple, est un bon candidat à la refactorisation. Si la boucle elle-même est déplacée vers le côté non managé, ou si une alternative managée à l’appel non managé est créée (par exemple, mettre des données en file d’attente sur le côté managé, puis les marshaler vers l’API non managée en même temps après la boucle), le nombre de transitions peut être considérablement réduit.

## <a name="pinvoke-vs-c-interop"></a>Appel P/Invoke et l’interopérabilité C++

Pour les langages .NET, tels que Visual Basic et C#, la méthode prescrite pour l’interopérabilité avec les composants natifs est P/Invoke. Étant donné que P/Invoke est pris en charge par le .NET Framework, Visual C++ le prend également en charge, mais Visual C++ fournit également sa propre prise en charge de l’interopérabilité, appelée interopérabilité C++. L’interopérabilité C++ est préférable à P/Invoke, car P/Invoke n’est pas de type sécurisé. Par conséquent, les erreurs sont essentiellement signalées au moment de l’exécution, mais l’interopérabilité C++ présente également des avantages en termes de performances par rapport à P/Invoke.

Les deux techniques requièrent plusieurs choses quand une fonction managée appelle une fonction non managée :

- Les arguments de l’appel de fonction sont marshalés du CLR vers les types natifs.

- Un thunk managé vers non managé est exécuté.

- La fonction non managée est appelée (à l’aide des versions natives des arguments).

- Un thunk non managé à managé est exécuté.

- Le type de retour et les arguments « out » ou « in, out » sont marshalés des types natifs à CLR.

Les thunks managés/non managés sont nécessaires pour que l’interopérabilité fonctionne, mais le marshaling de données requis dépend des types de données impliqués, de la signature de la fonction et de la façon dont les données sont utilisées.

Le marshaling de données effectué par l’interopérabilité C++ est la forme la plus simple possible : les paramètres sont simplement copiés dans la limite managée/non managée dans un mode de bits. aucune transformation n’est effectuée. Pour P/Invoke, cela est vrai uniquement si tous les paramètres sont des types blittables simples. Dans le cas contraire, P/Invoke exécute des étapes très robustes pour convertir chaque paramètre managé en un type natif approprié, et vice versa si les arguments sont marqués comme « out » ou « in, out ».

En d’autres termes, l’interopérabilité C++ utilise la méthode la plus rapide possible du marshaling de données, alors que P/Invoke utilise la méthode la plus fiable. Cela signifie que l’interopérabilité C++ (de manière classique pour C++) offre des performances optimales par défaut et que le programmeur est responsable de l’adressage des cas où ce comportement n’est pas sûr ou approprié.

Par conséquent, l’interopérabilité C++ exige que le marshaling de données soit fourni explicitement, mais l’avantage est que le programmeur est libre de déterminer ce qui est approprié, compte tenu de la nature des données et de la façon dont elles doivent être utilisées. En outre, même si le comportement du marshaling de données P/Invoke peut être modifié à un niveau personnalisé, l’interopérabilité C++ permet de personnaliser le marshaling des données au niveau de l’appel. Cela n’est pas possible avec P/Invoke.

Pour plus d’informations sur l’interopérabilité C++, consultez [utilisation de l’interopérabilité c++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

## <a name="see-also"></a>Voir aussi

[Assemblys mixtes (natifs et managés)](../dotnet/mixed-native-and-managed-assemblies.md)
