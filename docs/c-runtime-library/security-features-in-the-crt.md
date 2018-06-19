---
title: Fonctionnalités de sécurité dans la bibliothèque CRT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8195e9a7e37ac9fa9186118889d7717698d2b784
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
ms.locfileid: "34451808"
---
# <a name="security-features-in-the-crt"></a>Fonctionnalités de sécurité dans le CRT
De nombreuses anciennes fonctions CRT ont de nouvelles versions plus sécurisées. Si une fonction sécurisée existe, l'ancienne version moins sécurisée est marquée comme déconseillée et la nouvelle version a le suffixe `_s` ("sécurisé").  
  
 Dans ce contexte, le terme "déconseillé" signifie simplement que l'utilisation d'une fonction n'est pas recommandée ; il n'indique pas que la fonction est programmée pour être supprimée du CRT.  
  
 Les fonctions sécurisées n'empêchent pas ni ne corrigent les erreurs de sécurité ; en revanche, elles interceptent les erreurs lorsqu'elles se produisent. Elles effectuent des contrôles supplémentaires pour les conditions d'erreur et, en cas d'erreur, elles appellent un gestionnaire d'erreurs (consultez [Validation de paramètres](../c-runtime-library/parameter-validation.md)).  
  
 Par exemple, la fonction `strcpy` n'a aucun moyen de déterminer si la chaîne qu'elle copie est trop volumineuse pour sa mémoire tampon de destination. Toutefois, sa fonction sécurisée équivalente, `strcpy_s`, prend la taille de la mémoire tampon comme paramètre, ce qui lui permet de déterminer si un dépassement de mémoire tampon se produit. Si vous utilisez la fonction `strcpy_s` pour copier onze caractères dans une mémoire tampon de dix caractères, il s'agit d'une erreur de votre part. La fonction `strcpy_s` ne peut pas corriger votre erreur, mais elle peut la détecter et vous en informer en appelant le gestionnaire de paramètre non valide.  
  
## <a name="eliminating-deprecation-warnings"></a>Suppression des avertissements de désapprobation  
 Il existe plusieurs façons de supprimer les avertissements de désapprobation pour les anciennes fonctions moins sécurisées. La méthode la plus simple est de définir `_CRT_SECURE_NO_WARNINGS` ou d'utiliser le pragma [warning](../preprocessor/warning.md). Les deux options désactivent les avertissements de désapprobation, mais bien évidemment, les problèmes de sécurité à l'origine des avertissements existent toujours. Il est préférable de laisser les avertissements de désapprobation activés et de tirer parti des nouvelles fonctionnalités de sécurité CRT.  
  
 En C++, la méthode la plus simple est d'utiliser [Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md), qui dans de nombreux cas supprime les avertissements de désapprobation en remplaçant les appels aux fonctions déconseillées par des appels aux nouvelles versions sécurisées de ces fonctions. Par exemple, prenez l'appel déconseillé à `strcpy` :  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 L'affectation de la valeur 1 à `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` supprime l'avertissement en modifiant l'appel `strcpy` à `strcpy_s`, ce qui empêche les dépassements de mémoire tampon. Pour plus d'informations, consultez [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md).  
  
 Pour les fonctions déconseillées sans surcharges de modèle sécurisées, vous devez envisager de mettre à jour manuellement votre code pour utiliser les versions sécurisées.  
  
 Une autre source d'avertissements de désapprobation, sans rapport avec la sécurité, sont les fonctions POSIX. Remplacez les noms de fonction POSIX par leurs équivalents standard (par exemple, remplacez [access](../c-runtime-library/reference/access-crt.md) par [_access](../c-runtime-library/reference/access-waccess.md)), ou désactivez les avertissements de désapprobation POSIX en définissant `_CRT_NONSTDC_NO_WARNINGS`. Pour plus d’informations, consultez [Compatibilité](compatibility.md).  
  
## <a name="additional-security-features"></a>Fonctionnalités de sécurité supplémentaires  
 Voici quelques-unes des fonctions de sécurité :  
  
-   `Parameter Validation`. Les paramètres passés aux fonctions CRT sont validés, dans les fonctions sécurisées et dans de nombreuses versions préexistantes de ces fonctions. Ces validations sont :  
  
    -   Vérifier les valeurs **NULL** passées aux fonctions.  
  
    -   Vérifier la validité des valeurs énumérées.  
  
    -   Vérifier que les valeurs intégrales sont comprises dans des plages valides.  
  
-   Pour plus d’informations, consultez [Validation de paramètre](../c-runtime-library/parameter-validation.md).  
  
-   Un gestionnaire de paramètres non valides est également accessible au développeur. Lorsqu'un paramètre non valide est détecté, au lieu de déclarer et de quitter l'application, le CRT fournit un moyen de vérifier ces problèmes avec la fonction [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).  
  
-   `Sized Buffers`. Les fonctions sécurisées requièrent que la taille de la mémoire tampon soit passée à une fonction qui écrit dans une mémoire tampon. Les versions sécurisées valident que la mémoire tampon est assez large avant d'y écrire, ce qui permet d'éviter de graves erreurs de dépassement de mémoire tampon qui peuvent autoriser l'exécution de code malveillant. Ces fonctions retournent généralement le type de code d'erreur `errno` et appellent le gestionnaire de paramètre non valide si la taille de la mémoire tampon est trop petite. Les fonctions qui lisent les mémoires tampons d'entrée, telles que `gets`, ont des versions sécurisées qui nécessitent que vous spécifiez une taille maximale.  
  
-   `Null termination`. Certaines fonctions qui laissent des chaines potentiellement non terminées ont des versions sécurisées qui garantissent que ces chaînes se terminent correctement par null.  
  
-   `Enhanced error reporting`. Les fonctions sécurisées retournent des codes d'erreur contenant plus d'informations sur les erreurs que dans les fonctions préexistantes. Les fonctions sécurisées et de nombreuses fonctions préexistantes définissent désormais `errno` et retournent souvent le type de code `errno`, pour fournir un meilleur rapport d'erreurs.  
  
-   `Filesystem security`. Les API d'E/S de fichier sécurisées prennent en charge par défaut l'accès sécurisé aux fichiers.  
  
-   `Windows security`. Les API de traitement sécurisées appliquent des stratégies de sécurité et permettent de spécifier les listes de contrôle d'accès.  
  
-   `Format string syntax checking`. Les chaînes non valides sont détectées, par exemple, en utilisant des caractères de champ de type incorrect dans les chaines de format `printf`.  
  
## <a name="see-also"></a>Voir aussi  
 [Validation de paramètre](../c-runtime-library/parameter-validation.md)   
 [Sécuriser les surcharges de modèle](../c-runtime-library/secure-template-overloads.md)   
 [Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)