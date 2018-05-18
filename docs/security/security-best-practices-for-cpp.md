---
title: Meilleures pratiques de sécurité pour C++ | Documents Microsoft
ms.custom: ''
ms.date: 05/08/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- securitybestpracticesVC
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
author: mikeblome
ms.author: mikeblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a0ed67c85cbd42985448ef9eb1806931d1c294f
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="security-best-practices-for-c"></a>Meilleures pratiques de sécurité pour C++

Cet article contient des informations sur les outils et les pratiques de sécurité. Leur utilisation n'immunise pas les applications contre les attaques, mais réduit la probabilité que ces attaques réussissent.  
  
## <a name="visual-c-security-features"></a>Fonctionnalités de sécurité de Visual C++

 Ces fonctionnalités de sécurité sont intégrées dans le compilateur et l'éditeur de liens Visual C++ :  
  
 [/guard (Activer la protection du flux de contrôle)](../build/reference/guard-enable-control-flow-guard.md)  
 Indique au compilateur d'analyser le flux de contrôle pour rechercher les cibles d'appel indirectes au moment de la compilation, puis d'insérer du code afin de vérifier les cibles au moment de l'exécution.  
  
 [/GS (vérification de la sécurité des mémoires tampons)](../build/reference/gs-buffer-security-check.md)  
 Indique au compilateur d'insérer du code de détection de débordement dans les fonctions qui courent le risque d'être exploitées. Quand un débordement est détecté, l'exécution est arrêtée. Cette option est activée par défaut.  
  
 [/SAFESEH (L’image est dotée de gestionnaires d’exceptions sécurisés)](../build/reference/safeseh-image-has-safe-exception-handlers.md)  
 Indique à l'éditeur de liens d'inclure dans l'image de sortie une table contenant l'adresse de chaque gestionnaire d'exceptions. Au moment de l'exécution, le système d'exploitation utilise cette table pour s'assurer que seuls les gestionnaires d'exceptions légitimes sont exécutés. Cela contribue à empêcher l'exécution de gestionnaires d'exceptions introduits par une attaque malveillante au moment de l'exécution. Cette option est désactivée par défaut.  
  
 [/ NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (Compatible avec la prévention de l’exécution des données)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)  
 Ces options de l'éditeur de liens et du compilateur permettent la compatibilité avec la prévention de l'exécution des données (PED). PED protège l'UC contre l'exécution de pages ne contenant pas de code.  
  
 [/analyze (Analyse de code)](../build/reference/analyze-code-analysis.md)  
 Cette option du compilateur active l'analyse du code, qui signale les problèmes de sécurité potentiels, tels que le dépassement de la mémoire tampon, la mémoire non initialisée, le déréférencement de pointeur null et les fuites de mémoire. Cette option est désactivée par défaut. Pour plus d’informations, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
 [/DYNAMICBASE (Utiliser la randomisation du format d’espace d’adresse)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)  
 Cette option de l'éditeur de liens permet de générer une image exécutable qui peut être chargée à différents emplacements dans la mémoire au début de l'exécution. Cette option rend également l'emplacement de la pile en mémoire beaucoup moins prévisible.  
  
## <a name="security-enhanced-crt"></a>Sécurité CRT améliorée  
 La bibliothèque Runtime C (CRT) a été étendue afin d'inclure des versions sécurisées des fonctions qui présentent des risques de sécurité, par exemple, la fonction de copie de chaîne non contrôlée `strcpy`. Comme les versions plus anciennes et non sécurisées de ces fonctions sont déconseillées, elles entraînent des avertissements de compilation. Nous vous encourageons à utiliser les versions sécurisées de ces fonctions CRT plutôt que de supprimer les avertissements de compilation. Pour plus d'informations, consultez [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="safeint-library"></a>Bibliothèque SafeInt  
 [Bibliothèque SafeInt](../windows/safeint-library.md) aide à éviter les dépassements de capacité de nombre entier et d’autres erreurs exploitables qui peuvent se produire lorsque l’application effectue des opérations mathématiques. Le `SafeInt` bibliothèque inclut les [SafeInt, classe](../windows/safeint-class.md), le [SafeIntException, classe](../windows/safeintexception-class.md)et plusieurs [SafeInt, fonctions](../windows/safeint-functions.md).  
  
 La classe `SafeInt` protège contre les dépassements sur les entiers et les tentatives de division par zéro. Vous pouvez l'utiliser pour gérer les comparaisons entre des valeurs de types différents. Elle fournit des deux stratégies de gestion des erreurs. Dans la stratégie par défaut, la classe `SafeInt` lève une exception de classe `SafeIntException` pour signaler la raison pour laquelle une opération mathématique ne peut pas être exécutée. Dans la seconde stratégie, la classe `SafeInt` arrête l'exécution du programme. Vous pouvez également définir une stratégie personnalisée.  
  
 Chaque fonction `SafeInt` protège une opération mathématique d'une erreur exploitable. Vous pouvez utiliser deux types différents de paramètres sans les convertir en un même type. Pour protéger plusieurs opérations mathématiques, utilisez la classe `SafeInt`.  
  
## <a name="checked-iterators"></a>Itérateurs vérifiés  
 Un itérateur vérifié met en place des limites de conteneur. Par défaut, quand un itérateur vérifié est hors limites, il génère une exception et arrête l'exécution du programme. Un itérateur vérifié fournit d’autres niveaux de réponse qui dépendent des valeurs qui sont assignées au préprocesseur définit comme  **\_SECURE\_SCL\_lève** et  **\_ITÉRATEUR\_déboguer\_niveau**. Par exemple, sur  **\_ITÉRATEUR\_déboguer\_LEVEL = 2**, un itérateur vérifié fournit de nombreuses vérifications d’exactitude en mode débogage, qui sont accessibles à l’aide des assertions. Pour plus d’informations, consultez [itérateurs vérifiés](../standard-library/checked-iterators.md) et [ \_ITÉRATEUR\_déboguer\_niveau](../standard-library/iterator-debug-level.md).  
  
## <a name="code-analysis-for-managed-code"></a>Analyse du code managé  
 L'analyse du code managé, également appelée FxCop, vérifie la conformité des assemblys aux règles de conception du .NET Framework. FxCop analyse le code et les métadonnées de chaque assembly pour rechercher des défaillances dans les domaines suivants :  
  
-   Conception des bibliothèques  
  
-   Localisation  
  
-   Conventions d'attribution d'un nom  
  
-   Performances  
  
-   Sécurité  
  
## <a name="windows-application-verifier"></a>Windows Application Verifier  
 Application Verifier (AppVerifier) peut vous aider à identifier les problèmes éventuels de compatibilité, de stabilité et de sécurité des applications.  
  
 AppVerifier surveille la manière dont une application utilise le système d'exploitation. Il surveille le système de fichiers, le Registre, la mémoire et les API pendant l'exécution de l'application et recommande des correctifs du code source pour les problèmes qu'il découvre.  
  
 Vous pouvez utiliser AppVerifier pour :  
  
-   Tester les erreurs potentielles de compatibilité des applications, provoquées par des erreurs de programmation courantes.  
  
-   Rechercher dans une application des problèmes liés à la mémoire.  

-   Identifier des problèmes potentiels de sécurité dans une application.  
  
 AppVerifier fait partie de l’Application Compatibility Toolkit, qui est disponible à partir de la [compatibilité des applications](http://go.microsoft.com/fwlink/p/?linkid=91277) sur le site web TechNet.  
  

## <a name="windows-user-accounts"></a>Comptes utilisateur Windows  
 L'utilisation de comptes utilisateur Windows qui appartiennent au groupe Administrateurs expose les développeurs et, par extension, les clients aux risques de sécurité. Pour plus d’informations, consultez [en cours d’exécution en tant que membre du groupe utilisateurs](running-as-a-member-of-the-users-group.md) et [compte des contrôle utilisateur (UAC) a une incidence sur votre Application](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Conseils pour les canaux côté spéculatif d’exécution

Pour plus d’informations sur la façon d’identifier et d’atténuation contre les vulnérabilités de matériel exécution spéculative côté canal dans le logiciel de C++, consultez [Guide du développeur C++ pour les canaux du côté spéculatif d’exécution](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Voir aussi  
- <xref:System.Security>   
- [Sécurité](/dotnet/standard/security/index)   
- [Répercussions du contrôle de compte utilisateur sur votre application](how-user-account-control-uac-affects-your-application.md)
