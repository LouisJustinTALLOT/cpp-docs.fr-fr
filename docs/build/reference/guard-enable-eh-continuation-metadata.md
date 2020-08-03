---
title: /guard:ehcont (Activer les métadonnées de continuation EH)
description: 'Guide de référence de l’option de compilateur Microsoft C++/Guard : ehcont.'
ms.date: 06/03/2020
f1_keywords:
- /guard:ehcont
- VC.Project.VCCLCompilerTool.GuardEHContMetadata
helpviewer_keywords:
- /guard:ehcont
- /guard:ehcont compiler option
ms.openlocfilehash: 0c5a49d578e626d052aa9d132afbaee5686cb7a7
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520523"
---
# <a name="guardehcont-enable-eh-continuation-metadata"></a>/guard:ehcont (Activer les métadonnées de continuation EH)

Active la génération de métadonnées de continuation EH (EHCONT) par le compilateur.

## <a name="syntax"></a>Syntaxe

> **`/guard:ehcont`**[**`-`**]

## <a name="remarks"></a>Notes

**`/guard:ehcont`** Avec l’option, le compilateur génère une liste triée des adresses virtuelles relatives (RVA) de toutes les cibles de continuation de gestion des exceptions valides pour un binaire. Elle est utilisée pendant l’exécution de la et de la `NtContinue` `SetThreadContext` validation du pointeur d’instruction. Par défaut, **`/guard:ehcont`** est désactivé et doit être activé explicitement. Pour désactiver explicitement cette option, utilisez **`/guard:ehcont-`** .

L' **`/guard:ehcont`** option est disponible dans Visual Studio 2019 version 16,7 et versions ultérieures. La fonctionnalité est prise en charge pour les processus 64 bits sur un système d’exploitation 64 bits.

La [technologie d’application du transit de contrôle (cet)](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf) est une fonctionnalité de sécurité basée sur le matériel qui protège contre les attaques basées sur la programmation orientée retour (ROP). Il gère une « pile cachée » pour chaque pile des appels afin d’appliquer l’intégrité du workflow de contrôle.

Lorsque des piles cachées sont disponibles pour empêcher les attaques de ROP, les attaquants se déplacent pour utiliser d’autres techniques d’exploitation. Une technique qu’ils peuvent utiliser est de corrompre la valeur du pointeur d’instruction à l’intérieur de la structure du [contexte](/windows/win32/api/winnt/ns-winnt-context) . Cette structure est passée dans les appels système qui redirigent l’exécution d’un thread, tel que `NtContinue` , [`RtlRestoreContext`](/windows/win32/api/winnt/nf-winnt-rtlrestorecontext) et [`SetThreadContext`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadcontext) . La `CONTEXT` structure est stockée en mémoire. Le fait d’endommager le pointeur d’instruction qu’il contient peut entraîner le transfert de l’exécution par les appels système vers une adresse contrôlée par un attaquant. Actuellement, `NTContinue` peut être appelé avec n’importe quel point de continuation. C’est pourquoi il est essentiel de valider le pointeur d’instruction lorsque les piles cachées sont activées.

`RtlRestoreContext`et `NtContinue` sont utilisés pendant le déroulement d’exception de gestion structurée des exceptions (SEH) à dérouler au frame cible qui contient le **`__except`** bloc. Le pointeur d’instruction du **`__except`** bloc n’est pas censé se trouver sur la pile cachée, car il échouerait à la validation du pointeur d’instruction. Le **`/guard:ehcont`** commutateur du compilateur génère une « table de continuation Eh ». Elle contient une liste triée des adresses RVA de toutes les cibles de continuation de gestion des exceptions valides dans le fichier binaire. `NtContinue`vérifie d’abord la pile d’ombres pour le pointeur d’instruction fourni par l’utilisateur, et si le pointeur d’instruction est introuvable, il poursuit la vérification de la table de continuation EH du binaire qui contient le pointeur d’instruction. Si le fichier binaire conteneur n’a pas été compilé avec la table, pour la compatibilité avec les binaires hérités, `NtContinue` est autorisé à continuer. Il est important de faire la distinction entre les binaires hérités qui n’ont pas de données EHCONT et les fichiers binaires contenant des données EHCONT, mais pas d’entrées de table. La première permet d’autoriser toutes les adresses à l’intérieur du fichier binaire comme cibles de continuation valides. Ce dernier n’autorise aucune adresse dans le fichier binaire en tant que cible de continuation valide.

L' **`/guard:ehcont`** option doit être passée à la fois au compilateur et à l’éditeur de liens pour générer des adresses RVA de continuation de type Eh pour un binaire. Si votre fichier binaire est généré à l'aide d'une seule commande `cl` , le compilateur passe l'option à l'éditeur de liens. Le compilateur passe également l' [**`/guard:cf`**](guard-enable-control-flow-guard.md) option à l’éditeur de liens. Si vous compilez et liez séparément, ces options doivent être définies à la fois sur les commandes du compilateur et de l’éditeur de liens.

Vous pouvez lier le code compilé à l’aide des **`/guard:ehcont`** bibliothèques et des fichiers objets compilés sans celui-ci. L’éditeur de liens retourne une erreur irrécupérable dans l’un des scénarios suivants :

- Une section de code a un « déroulement local ». Pour plus d’informations, consultez arrêt anormal dans [une instruction try-finally](../../cpp/try-finally-statement.md#abnormal-termination).

- Une section EH (XData) contient des pointeurs vers une section de code, et ils ne sont pas destinés à SEH.

- Les pointeurs sont pour SEH, mais le fichier objet n’a pas été compilé à l’aide de la liaison au niveau des fonctions ([/Gy](gy-enable-function-level-linking.md)) pour produire des COMDAT.

L’éditeur de liens retourne une erreur irrécupérable, car il ne peut pas générer de métadonnées dans ces scénarios. Cela signifie que la levée d’une exception est susceptible de provoquer un blocage au moment de l’exécution.

Pour les informations de section SEH trouvées dans les COMDAT, mais non compilées à l’aide de **`/guard:ehcont`** , l’éditeur de liens émet un avertissement **LNK4291**. Dans ce cas, l’éditeur de liens génère des métadonnées correctes mais conservatrices pour la section. Pour ignorer cet avertissement, utilisez [/ignore (ignorer des avertissements spécifiques)](ignore-ignore-specific-warnings.md).

Si l’éditeur de liens n’est pas en mesure de générer des métadonnées, il émet l’une des erreurs suivantes :

- `LNK2046: module contains _local_unwind but was not compiled with /guard:ehcont`

- `LNK2047: module contains C++ EH or complex EH metadata but was not compiled with /guard:ehcont.`

Pour vérifier si un fichier binaire contient des données EHCONT, recherchez les éléments suivants lors du vidage de la configuration de chargement du fichier binaire :

```cmd
e:\>link /dump /loadconfig CETTest.exe
...
            10417500 Guard Flags
...
                       EH Continuation table present      // EHCONT guard flag present
...
    0000000180018640 Guard EH continuation table
                  37 Guard EH continuation count          // May be 0 if no exception handling is used in the binary. Still counts has having EHCONT data.
...
    Guard EH Continuation Table                           // List of RVAs

          Address
          --------
           0000000180002CF5
           0000000180002F03
           0000000180002F0A
...
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >  **C/C++**  >  **génération de code** .

1. Sélectionnez la propriété **activer les métadonnées de continuation Eh** .

1. Dans le contrôle de liste déroulante, choisissez **Oui (/Guard : ehcont)** pour activer les métadonnées de continuation Eh, ou **non (/Guard : ehcont-)** pour la désactiver.

## <a name="see-also"></a>Voir aussi

[/Guard (activer la protection du contrôle de Workflow)](guard-enable-control-flow-guard.md)\
[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
