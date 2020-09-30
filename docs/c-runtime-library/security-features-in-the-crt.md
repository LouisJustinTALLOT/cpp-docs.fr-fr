---
title: Fonctionnalités de sécurité dans le CRT
description: Vue d’ensemble des fonctions CRT sécurisées dans le runtime C de Microsoft.
ms.date: 09/29/2020
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
ms.openlocfilehash: 963f5510350aa3be25586811889189d28a5f7b66
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589885"
---
# <a name="security-features-in-the-crt"></a>Fonctionnalités de sécurité dans le CRT

De nombreuses anciennes fonctions CRT ont de nouvelles versions plus sécurisées. Si une fonction sécurisée existe, l'ancienne version moins sécurisée est marquée comme déconseillée et la nouvelle version a le suffixe `_s` ("sécurisé").

Dans ce contexte, « déconseillé » signifie que l’utilisation de la fonction n’est pas recommandée. Cela ne signifie pas que la fonction est planifiée pour être supprimée du CRT.

Les fonctions sécurisées n’empêchent pas ni ne corrigent les erreurs de sécurité. Au lieu de cela, ils interceptent les erreurs lorsqu’ils se produisent. Elles effectuent des vérifications supplémentaires pour les conditions d’erreur. En cas d’erreur, elles appellent un gestionnaire d’erreurs (consultez [validation de paramètre](../c-runtime-library/parameter-validation.md)).

Par exemple, la `strcpy` fonction ne peut pas déterminer si la chaîne qu’elle copie est trop grande pour la mémoire tampon de destination. Son équivalent sécurisé, `strcpy_s` , prend la taille de la mémoire tampon en tant que paramètre. Il peut ainsi déterminer si un dépassement de mémoire tampon se produit. Si vous utilisez `strcpy_s` pour copier 11 caractères dans une mémoire tampon de 10 caractères, il s’agit d’une erreur de votre part, vous `strcpy_s` ne pouvez pas corriger votre erreur. Mais il peut détecter votre erreur et vous en informer en appelant le gestionnaire de paramètre non valide.

## <a name="eliminating-deprecation-warnings"></a>Suppression des avertissements de désapprobation

Il existe plusieurs façons de supprimer les avertissements de désapprobation pour les anciennes fonctions moins sécurisées. La méthode la plus simple est de définir `_CRT_SECURE_NO_WARNINGS` ou d'utiliser le pragma [warning](../preprocessor/warning.md). Désactivez les avertissements de désapprobation, mais les problèmes de sécurité qui ont provoqué les avertissements existent toujours. Il est préférable de conserver les avertissements de désapprobation activés et de tirer parti des nouvelles fonctionnalités de sécurité CRT.

En C++, le moyen le plus simple de le faire consiste à utiliser des [surcharges de modèle sécurisées](../c-runtime-library/secure-template-overloads.md). Cela élimine les avertissements de désapprobation, dans de nombreux cas, en remplaçant les appels aux fonctions déconseillées par des appels à des versions sécurisées de ces fonctions. Par exemple, prenez l'appel déconseillé à `strcpy` :

```
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

L'affectation de la valeur 1 à `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` supprime l'avertissement en modifiant l'appel `strcpy` à `strcpy_s`, ce qui empêche les dépassements de mémoire tampon. Pour plus d’informations, consultez [Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md).

Pour les fonctions déconseillées sans surcharges de modèle sécurisées, vous devez envisager de mettre à jour manuellement votre code pour utiliser les versions sécurisées.

Une autre source d'avertissements de désapprobation, sans rapport avec la sécurité, sont les fonctions POSIX. Remplacez les noms de fonction POSIX par leurs équivalents standard (par exemple, remplacez [access](../c-runtime-library/reference/access-crt.md) par [_access](../c-runtime-library/reference/access-waccess.md)), ou désactivez les avertissements de désapprobation POSIX en définissant `_CRT_NONSTDC_NO_WARNINGS`. Pour plus d’informations, consultez [Compatibilité](compatibility.md).

## <a name="additional-security-features"></a>Fonctionnalités de sécurité supplémentaires

Voici quelques-unes des fonctionnalités de sécurité :

- `Parameter Validation`. Les fonctions sécurisées, ainsi que la plupart de leurs équivalents non sécurisés, valident les paramètres. La validation peut inclure :

  - Vérification de la présence de valeurs **null** .
  - Vérifier la validité des valeurs énumérées.
  - Vérifier que les valeurs intégrales sont comprises dans des plages valides.

- Pour plus d’informations, consultez [Validation de paramètre](../c-runtime-library/parameter-validation.md).

- Un gestionnaire de paramètres non valides est également accessible au développeur. Lorsqu’une fonction rencontre un paramètre non valide, au lieu de déclarer et de quitter l’application, le CRT vous permet de vérifier ces problèmes via [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

- `Sized Buffers`. Vous devez passer la taille de la mémoire tampon à toute fonction sécurisée qui écrit dans une mémoire tampon. Les versions sécurisées valident que la mémoire tampon est suffisamment grande pour pouvoir y écrire. Ce qui permet d’éviter les erreurs de dépassement de mémoire tampon dangereuses qui pourraient permettre l’exécution de code malveillant. Ces fonctions retournent généralement un `errno` code d’erreur et appellent le gestionnaire de paramètre non valide si la taille de la mémoire tampon est trop petite. Les fonctions qui lisent les mémoires tampons d'entrée, telles que `gets`, ont des versions sécurisées qui nécessitent que vous spécifiez une taille maximale.

- `Null termination`. Certaines fonctions qui ont quitté des chaînes potentiellement non terminées ont des versions sécurisées qui garantissent que les chaînes se terminent correctement par un caractère null.

- `Enhanced error reporting`. Les fonctions sécurisées retournent des codes d’erreur avec davantage d’informations d’erreur que celles disponibles avec les fonctions préexistantes. Les fonctions sécurisées et de nombreuses fonctions préexistantes sont désormais définies `errno` et retournent souvent un `errno` type de code, pour fournir un meilleur rapport d’erreurs.

- `Filesystem security`. Les API d'E/S de fichier sécurisées prennent en charge par défaut l'accès sécurisé aux fichiers.

- `Windows security`. Les API de traitement sécurisées appliquent des stratégies de sécurité et permettent de spécifier les listes de contrôle d'accès.

- `Format string syntax checking`. Les chaînes non valides sont détectées, par exemple, en utilisant des caractères de champ de type incorrect dans les chaines de format `printf`.

## <a name="see-also"></a>Voir aussi

[Validation de paramètre](../c-runtime-library/parameter-validation.md)<br/>
[Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md)<br/>
[Fonctionnalités de la bibliothèque CRT](../c-runtime-library/crt-library-features.md)
