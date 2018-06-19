---
title: Considérations sur les performances de l’interopérabilité (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9223c52e4ef831a9a1ff657db1a0d7859dd6ce6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164048"
---
# <a name="performance-considerations-for-interop-c"></a>Considérations sur les performances de l'interopérabilité (C++)
Cette rubrique fournit des recommandations pour réduire l’effet de transitions d’interopérabilité managés/non managés non sur les performances d’exécution.  
  
 Visual C++ prend en charge les mêmes mécanismes d’interopérabilité que d’autres langages .NET tels que Visual Basic et c# (P/Invoke), mais il fournit également la prise en charge de l’interopérabilité spécifique à Visual C++ (interopérabilité C++). Pour les applications critiques pour les performances, il est important de comprendre les implications de performances de chaque technique d’interopérabilité.  
  
 Quelle que soit la technique d’interopérabilité utilisée, des séquences de transition spéciales appelées thunks sont requis chaque fois qu’une fonction managée appelle une versa non managé de fonction et inversement. Ces thunks sont insérés automatiquement par le compilateur Visual C++, mais il est important de garder à l’esprit qu’ensemble, ces transitions peuvent être coûteuses en termes de performances.  
  
## <a name="reducing-transitions"></a>Réduction des Transitions  
 Un pour éviter ou réduire le coût des thunks d’interopérabilité consiste à refactoriser les interfaces impliquées afin de réduire les transitions managées/non managées. Améliore les performances peut être effectuées en ciblant les interfaces bavardes sont celles qui impliquent des appels fréquents entre la limite managée /. Une fonction managée qui appelle une fonction non managée dans une boucle serrée, est, par exemple, un bon candidat pour la refactorisation. Si la boucle elle-même est déplacée vers le côté non managé, ou si une alternative managée à l’appel non managé est créée (peut-être être des files d’attente de données du côté managé et son marshaling à l’API non managée à la fois après la boucle), le nombre de transitions peut être réduite de signe ificantly.  
  
## <a name="pinvoke-vs-c-interop"></a>Vs de P/Invoke. Interopérabilité C++  
 Pour les langages .NET, tels que Visual Basic et c#, la méthode prescrite pour interagir avec des composants natifs est P/Invoke. P/Invoke est pris en charge par le .NET Framework, Visual C++ prend également en charge, mais Visual C++ fournit aussi sa propre prise en charge de l’interopérabilité, qui est appelé interopérabilité C++. Interopérabilité C++ est préférable P/Invoke, car P/Invoke n’est pas un type sécurisé. Par conséquent, principalement les erreurs sont signalées au moment de l’exécution, mais interopérabilité C++ a également les avantages de performances P/Invoke.  
  
 Ces deux techniques nécessitent plusieurs choses se produire chaque fois qu’une fonction managée appelle une fonction non managée :  
  
-   Les arguments d’appel de fonction sont marshalés vers des types natifs du CLR.  
  
-   Un thunk non managés est exécuté.  
  
-   La fonction non managée est appelée (à l’aide des versions natives des arguments).  
  
-   Une conversion de code managé à managé est exécutée.  
  
-   Le type de retour et de « sortie » ou « dans, out » les arguments sont marshalés du code natif pour les types CLR.  
  
 Les thunks managés/non managés non sont nécessaires pour interop fonctionne, mais le marshaling de données qui est requis dépend des types de données impliqués, la signature de fonction et comment les données seront utilisées.  
  
 Le marshaling de données effectuées par l’interopérabilité C++ est la forme la plus simple possible : les paramètres sont copiés entre la limite managée/de manière au niveau du bit ; Aucune transformation n’est effectuée. Pour les P/Invoke, cela est vrai uniquement si tous les paramètres sont simples, des types blittables. Sinon, P/Invoke effectue des étapes très robustes pour convertir chaque paramètre managé en un type natif approprié, et inversement si les arguments sont marqués comme « out », ou « dans, out ».  
  
 En d’autres termes, interopérabilité C++ utilise la méthode la plus rapide possible de marshaling de données, alors que P/Invoke utilise la méthode la plus fiable. Cela signifie que l’interopérabilité C++ (dans une manière propre à C++) fournit des performances optimales par défaut, et que le programmeur est chargé de résoudre les cas où ce comportement n’est pas sûr ou approprié.  
  
 Interopérabilité C++ nécessite par conséquent que le marshaling de données doit être fourni explicitement, mais l’avantage est que le programmeur est libre de décider ce qui est approprié, en fonction de la nature des données, et comment il doit être utilisé. En outre, bien que le comportement de marshaling de données de P/Invoke peut être modifié et personnalisé à un degré, interopérabilité C++ permet de personnaliser chaque appel appel le marshaling de données. Cela n’est pas possible avec P/Invoke.  
  
 Pour plus d’informations sur l’interopérabilité C++, consultez [à l’aide du interopérabilité C++ (PInvoke implicite)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Assemblys mixtes (natif et managé)](../dotnet/mixed-native-and-managed-assemblies.md)