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
ms.openlocfilehash: 12b2db55a393928683e65c8faca49595fbbebc51
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87389959"
---
# <a name="security-best-practices-for-c"></a>Meilleures pratiques de sécurité pour C++

Cet article contient des informations sur les outils et les pratiques de sécurité. Leur utilisation n'immunise pas les applications contre les attaques, mais réduit la probabilité que ces attaques réussissent.

## <a name="visual-c-security-features"></a>Fonctionnalités de sécurité de Visual C++

Ces fonctionnalités de sécurité sont intégrées au compilateur et à l’éditeur de liens Microsoft C++ :

[`/guard`(Activer la protection du contrôle de Workflow)](../build/reference/guard-enable-control-flow-guard.md)<br/>
Indique au compilateur d’analyser le workflow pour les cibles d’appel indirect au moment de la compilation, puis d’insérer du code pour vérifier les cibles au moment de l’exécution.

[`/GS`(Vérification de sécurité de la mémoire tampon)](../build/reference/gs-buffer-security-check.md)<br/>
Indique au compilateur d'insérer du code de détection de débordement dans les fonctions qui courent le risque d'être exploitées. Quand un débordement est détecté, l'exécution est arrêtée. Cette option est activée par défaut.

[`/SAFESEH`(L’image a des gestionnaires d’exceptions sécurisés)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
Indique à l'éditeur de liens d'inclure dans l'image de sortie une table contenant l'adresse de chaque gestionnaire d'exceptions. Au moment de l'exécution, le système d'exploitation utilise cette table pour s'assurer que seuls les gestionnaires d'exceptions légitimes sont exécutés. Cela contribue à empêcher l'exécution de gestionnaires d'exceptions introduits par une attaque malveillante au moment de l'exécution. Par défaut, cette option est désactivée.

[`/NXCOMPAT`](../build/reference/nxcompat.md), [ `/NXCOMPAT` (Compatible avec la prévention de l’exécution des données)](../build/reference/nxcompat-compatible-with-data-execution-prevention.md) ces options du compilateur et de l’éditeur de liens activent la compatibilité avec la prévention de l’exécution des données (DEP). PED protège l'UC contre l'exécution de pages ne contenant pas de code.

[`/analyze`(Analyse du code)](../build/reference/analyze-code-analysis.md)<br/>
Cette option du compilateur active l'analyse du code, qui signale les problèmes de sécurité potentiels, tels que le dépassement de la mémoire tampon, la mémoire non initialisée, le déréférencement de pointeur null et les fuites de mémoire. Par défaut, cette option est désactivée. Pour plus d’informations, consultez [vue d’ensemble de l’analyse du code pour C/C++](/cpp/code-quality/code-analysis-for-c-cpp-overview).

[`/DYNAMICBASE`(Utiliser la randomisation du format d’espace d’adresse)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
Cette option de l'éditeur de liens permet de générer une image exécutable qui peut être chargée à différents emplacements dans la mémoire au début de l'exécution. Cette option rend également l'emplacement de la pile en mémoire beaucoup moins prévisible.

## <a name="security-enhanced-crt"></a>Sécurité CRT améliorée

La bibliothèque Runtime C (CRT) a été étendue afin d'inclure des versions sécurisées des fonctions qui présentent des risques de sécurité, par exemple, la fonction de copie de chaîne non contrôlée `strcpy`. Comme les versions plus anciennes et non sécurisées de ces fonctions sont déconseillées, elles entraînent des avertissements de compilation. Nous vous encourageons à utiliser les versions sécurisées de ces fonctions CRT plutôt que de supprimer les avertissements de compilation. Pour plus d'informations, consultez [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="safeint-library"></a>Bibliothèque SafeInt

La [bibliothèque SafeInt](../safeint/safeint-library.md) permet d’éviter les débordements d’entiers et d’autres erreurs exploitables qui peuvent se produire lorsque l’application effectue des opérations mathématiques. La `SafeInt` bibliothèque comprend la [classe SafeInt](../safeint/safeint-class.md), la [classe SafeIntException](../safeint/safeintexception-class.md)et plusieurs [fonctions SafeInt](../safeint/safeint-functions.md).

La classe `SafeInt` protège contre les dépassements sur les entiers et les tentatives de division par zéro. Vous pouvez l'utiliser pour gérer les comparaisons entre des valeurs de types différents. Il fournit deux stratégies de gestion des erreurs. Dans la stratégie par défaut, la classe `SafeInt` lève une exception de classe `SafeIntException` pour signaler la raison pour laquelle une opération mathématique ne peut pas être exécutée. Dans la seconde stratégie, la classe `SafeInt` arrête l'exécution du programme. Vous pouvez également définir une stratégie personnalisée.

Chaque fonction `SafeInt` protège une opération mathématique d'une erreur exploitable. Vous pouvez utiliser deux types différents de paramètres sans les convertir en un même type. Pour protéger plusieurs opérations mathématiques, utilisez la classe `SafeInt`.

## <a name="checked-iterators"></a>Checked Iterators

Un itérateur vérifié met en place des limites de conteneur. Par défaut, quand un itérateur vérifié est hors limites, il génère une exception et arrête l'exécution du programme. Un itérateur vérifié fournit d’autres niveaux de réponse qui dépendent des valeurs affectées aux définitions de préprocesseur, telles que `_SECURE_SCL_THROWS` et `_ITERATOR_DEBUG_LEVEL` . Par exemple, au niveau de `_ITERATOR_DEBUG_LEVEL=2` , un itérateur vérifié fournit des vérifications d’exactitude complètes en mode débogage, qui sont rendues disponibles à l’aide d’assertions. Pour plus d’informations, consultez [itérateurs vérifiés](../standard-library/checked-iterators.md) et [`_ITERATOR_DEBUG_LEVEL`](../standard-library/iterator-debug-level.md) .

## <a name="code-analysis-for-managed-code"></a>Analyse du code managé

L'analyse du code managé, également appelée FxCop, vérifie la conformité des assemblys aux règles de conception du .NET Framework. FxCop analyse le code et les métadonnées de chaque assembly pour rechercher des défaillances dans les domaines suivants :

- Conception des bibliothèques

- Localisation

- Conventions d'attribution d'un nom

- Performances

- Sécurité

## <a name="windows-application-verifier"></a>Windows Application Verifier

Le [Application Verifier (AppVerifier)](/windows-hardware/drivers/debugger/enable-application-verifier) peut vous aider à identifier les problèmes potentiels de compatibilité, de stabilité et de sécurité des applications.

AppVerifier surveille la manière dont une application utilise le système d'exploitation. Il surveille le système de fichiers, le Registre, la mémoire et les API pendant l'exécution de l'application et recommande des correctifs du code source pour les problèmes qu'il découvre.

Vous pouvez utiliser AppVerifier pour :

- Tester les erreurs potentielles de compatibilité des applications, provoquées par des erreurs de programmation courantes.

- Rechercher dans une application des problèmes liés à la mémoire.

- Identifier des problèmes potentiels de sécurité dans une application.

## <a name="windows-user-accounts"></a>Comptes utilisateur Windows

L'utilisation de comptes utilisateur Windows qui appartiennent au groupe Administrateurs expose les développeurs et, par extension, les clients aux risques de sécurité. Pour plus d’informations, consultez [exécuter en tant que membre du groupe utilisateurs](running-as-a-member-of-the-users-group.md) et [Comment le contrôle de compte d’utilisateur (UAC) affecte votre application](how-user-account-control-uac-affects-your-application.md).

## <a name="guidance-for-speculative-execution-side-channels"></a>Conseils pour les canaux côté exécution spéculative

Pour plus d’informations sur la façon de faciliteront son identification et d’atténuer les vulnérabilités matérielles du canal côté exécution spéculative dans le logiciel C++, consultez [Guide du développeur c++ pour les canaux côté exécution spéculative](developer-guidance-speculative-execution.md).

## <a name="see-also"></a>Voir aussi

<xref:System.Security> <br/>
[Sécurité](/dotnet/standard/security/index)<br/>
[Répercussions du contrôle de compte d’utilisateur (UAC) sur votre application](how-user-account-control-uac-affects-your-application.md)
