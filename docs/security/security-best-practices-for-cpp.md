---
title: Meilleures pratiques de sécurité pour C++
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: 914498a79d3d3ddae08ae672aac35c6e913ef238
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988073"
---
# <a name="security-best-practices-for-c"></a>Meilleures pratiques de sécurité pour C++

Cet article contient des informations sur les outils et les pratiques de sécurité. Leur utilisation n'immunise pas les applications contre les attaques, mais réduit la probabilité que ces attaques réussissent.

## <a name="visual-c-security-features"></a>Fonctionnalités de sécurité de Visual C++

These security features are built into the Microsoft C++ compiler and linker:

[/guard (Activer la protection du flux de contrôle)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Causes the compiler to analyze control flow for indirect call targets at compile time, and then to insert code to verify the targets at runtime.

[/GS (vérification de la sécurité des mémoires tampons)](../build/reference/gs-buffer-security-check.md)<br/>
Indique au compilateur d'insérer du code de détection de débordement dans les fonctions qui courent le risque d'être exploitées. Quand un débordement est détecté, l'exécution est arrêtée. Cette option est activée par défaut.

[/SAFESEH (L’image est dotée de gestionnaires d’exceptions sécurisés)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Indique à l'éditeur de liens d'inclure dans l'image de sortie une table contenant l'adresse de chaque gestionnaire d'exceptions. Au moment de l'exécution, le système d'exploitation utilise cette table pour s'assurer que seuls les gestionnaires d'exceptions légitimes sont exécutés. Cela contribue à empêcher l'exécution de gestionnaires d'exceptions introduits par une attaque malveillante au moment de l'exécution. Cette option est désactivée par défaut.

[/NXCOMPAT](../build/reference/nxcompat.md), [/NXCOMPAT (Compatible with Data Execution Prevention)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) These compiler and linker options enable Data Execution Prevention (DEP) compatibility. PED protège l'UC contre l'exécution de pages ne contenant pas de code.

[/analyze (Analyse de code)](../build/reference/analyze-code-analysis.md)<br/>
Cette option du compilateur active l'analyse du code, qui signale les problèmes de sécurité potentiels, tels que le dépassement de la mémoire tampon, la mémoire non initialisée, le déréférencement de pointeur null et les fuites de mémoire. Cette option est désactivée par défaut. For more information, see [Code Analysis for C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).

[/DYNAMICBASE (Utiliser la randomisation du format d’espace d’adresse)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Cette option de l'éditeur de liens permet de générer une image exécutable qui peut être chargée à différents emplacements dans la mémoire au début de l'exécution. Cette option rend également l'emplacement de la pile en mémoire beaucoup moins prévisible.

## <a name="security-enhanced-crt"></a>Sécurité CRT améliorée

La bibliothèque Runtime C (CRT) a été étendue afin d'inclure des versions sécurisées des fonctions qui présentent des risques de sécurité, par exemple, la fonction de copie de chaîne non contrôlée `strcpy`. Comme les versions plus anciennes et non sécurisées de ces fonctions sont déconseillées, elles entraînent des avertissements de compilation. Nous vous encourageons à utiliser les versions sécurisées de ces fonctions CRT plutôt que de supprimer les avertissements de compilation. Pour plus d'informations, consultez [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>Bibliothèque SafeInt

[SafeInt Library](../safeint/safeint-library.md) helps prevent integer overflows and other exploitable errors that might occur when the application performs mathematical operations. The `SafeInt` library includes the [SafeInt Class](../safeint/safeint-class.md), the [SafeIntException Class](../safeint/safeintexception-class.md), and several [SafeInt Functions](../safeint/safeint-functions.md).

La classe `SafeInt` protège contre les dépassements sur les entiers et les tentatives de division par zéro. Vous pouvez l'utiliser pour gérer les comparaisons entre des valeurs de types différents. It provides two error handling policies. Dans la stratégie par défaut, la classe `SafeInt` lève une exception de classe `SafeIntException` pour signaler la raison pour laquelle une opération mathématique ne peut pas être exécutée. Dans la seconde stratégie, la classe `SafeInt` arrête l'exécution du programme. Vous pouvez également définir une stratégie personnalisée.

Chaque fonction `SafeInt` protège une opération mathématique d'une erreur exploitable. Vous pouvez utiliser deux types différents de paramètres sans les convertir en un même type. Pour protéger plusieurs opérations mathématiques, utilisez la classe `SafeInt`.

## <a name="checked-iterators"></a>itérateurs vérifiés

Un itérateur vérifié met en place des limites de conteneur. Par défaut, quand un itérateur vérifié est hors limites, il génère une exception et arrête l'exécution du programme. A checked iterator provides other levels of response that depend on values that are assigned to preprocessor defines such as **\_SECURE\_SCL\_THROWS** and **\_ITERATOR\_DEBUG\_LEVEL**. For example, at **\_ITERATOR\_DEBUG\_LEVEL=2**, a checked iterator provides comprehensive correctness checks in debug mode, which are made available by using asserts. For more information, see [Checked Iterators](../standard-library/checked-iterators.md) and [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md).

## <a name="code-analysis-for-managed-code"></a>Analyse du code managé

L'analyse du code managé, également appelée FxCop, vérifie la conformité des assemblys aux règles de conception du .NET Framework. FxCop analyse le code et les métadonnées de chaque assembly pour rechercher des défaillances dans les domaines suivants :

- Conception des bibliothèques

- Localisation

- Conventions d'attribution d'un nom

- Performances

- Sécurité

## <a name="windows-application-verifier"></a>Windows Application Verifier

The [Application Verifier (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) can help you identify potential application compatibility, stability, and security issues.

AppVerifier surveille la manière dont une application utilise le système d'exploitation. Il surveille le système de fichiers, le Registre, la mémoire et les API pendant l'exécution de l'application et recommande des correctifs du code source pour les problèmes qu'il découvre.

Vous pouvez utiliser AppVerifier pour :

- Tester les erreurs potentielles de compatibilité des applications, provoquées par des erreurs de programmation courantes.

- Rechercher dans une application des problèmes liés à la mémoire.

- Identifier des problèmes potentiels de sécurité dans une application.

## <a name="windows-user-accounts"></a>Comptes utilisateur Windows

L'utilisation de comptes utilisateur Windows qui appartiennent au groupe Administrateurs expose les développeurs et, par extension, les clients aux risques de sécurité. For more information, see [Running as a Member of the Users Group](running-as-a-member-of-the-users-group.md) and [How User Account Control (UAC) Affects Your Application](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Guidance for Speculative Execution Side Channels

For information about how to indentify and mitigate against speculative execution side channel hardware vulnerabilities in C++ software, see [C++ Developer Guidance for Speculative Execution Side Channels](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Voir aussi

<xref:System.Security> <br/>
[Security](/dotnet/standard/security/index)<br/>
[Répercussions du contrôle de compte utilisateur sur votre application](how-user-account-control-uac-affects-your-application.md)
