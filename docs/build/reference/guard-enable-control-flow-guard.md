---
title: /guard (Activer la protection du flux de contrôle)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: 8b15318ab7ae4233d6cf02a505ffe901bbe1d689
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50516071"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (Activer la protection du flux de contrôle)

Active la génération par le compilateur de vérifications de sécurité de la protection du flux de contrôle.

## <a name="syntax"></a>Syntaxe

```
/guard:cf[-]
```

## <a name="remarks"></a>Notes

L'option **/guard:cf** indique au compilateur d'analyser le flux de contrôle pour rechercher les cibles d'appels indirects au moment de la compilation, puis d'insérer du code pour vérifier les cibles au moment de l'exécution. Par défaut, l'option **/guard:cf** est désactivée. Elle doit être explicitement activée. Pour désactiver explicitement cette option, utilisez **/guard:cf-**.

**Visual Studio 2017 et versions ultérieur**: cette option ajoute gardes pour **basculer** instructions qui génèrent des raccourcis de tables.

Quand l'option de protection du flux de contrôle **/guard:cf** est activée, le compilateur et l'éditeur de liens incluent d'autres vérifications de sécurité à l'exécution pour détecter les tentatives visant à compromettre votre code. Pendant les phases de compilation et de liaison, tous les appels indirects dans votre code sont analysés pour identifier chaque emplacement auquel le code peut accéder quand il s'exécute correctement. Ces informations sont stockées dans des structures supplémentaires dans les en-têtes de vos fichiers binaires. Le compilateur injecte également une vérification avant chaque appel indirect dans votre code pour garantir que la cible fait partie des emplacements vérifiés. Si la vérification échoue à l'exécution sur un système d'exploitation utilisant la protection du flux de contrôle, le système d'exploitation ferme le programme.

Une attaque courante sur les logiciels exploite certains bogues dans la gestion des valeurs extrêmes ou inattendues. Une valeur judicieusement ajoutée à l'application peut remplacer un emplacement qui contient un pointeur vers le code exécutable. Cette entrée peut alors servir à rediriger le flux de contrôle vers du code contrôlé par l'attaquant. Les vérifications à l'exécution de la protection du flux de contrôle ne corrigent pas les bogues d'altération des données dans votre fichier exécutable. En fait, elles rendent plus difficile pour un attaquant d'exploiter ces bogues pour exécuter du code arbitraire. La protection du flux de contrôle est un outil qui contribue à empêcher les appels ciblant des emplacements autres que les points d'entrée de fonction dans votre code. Elle fonctionne de façon similaire à la prévention de l'exécution des données (PED), aux vérifications de pile  [/GS](../../build/reference/gs-buffer-security-check.md) et à la randomisation du format d'espace d'adresse (ASLR) [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) et [/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md) qui réduisent aussi les risques d'utilisation de votre code en vecteur d'attaque.

L'option **/guard:cf** doit être passée à la fois au compilateur et à l'éditeur de liens pour générer le code qui utilise la protection du flux de contrôle pour atténuer les risques d'attaque. Si votre fichier binaire est généré à l'aide d'une seule commande `cl` , le compilateur passe l'option à l'éditeur de liens. Si vous effectuez la compilation et la liaison séparément, l'option doit être spécifiée dans les commandes du compilateur et de l'éditeur de liens. L'option /DYNAMICBASE de l'éditeur de liens doit également être spécifiée. Pour vérifier si votre fichier binaire contient des données de protection du flux de contrôle, utilisez la commande `dumpbin /headers /loadconfig` . Quand les fichiers binaires sont définis avec une protection du flux de contrôle, `Guard` figure dans la liste des caractéristiques EXE ou DLL, et les indicateurs de protection Guard `CF Instrumented` et `FID table present`.

L'option **/guard:cf** n'est pas compatible avec les options [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) (informations de débogage Modifier &amp; Continuer) et [/clr](../../build/reference/clr-common-language-runtime-compilation.md) (compilation pour le Common Language Runtime).

Le code compilé avec l'option **/guard:cf** peut être lié à des bibliothèques et fichiers objet qui ne sont pas compilés avec cette option. La protection du flux de contrôle est activée pour ce code uniquement, si le code est également lié avec l'option **/guard:cf** et exécuté sur un système d'exploitation utilisant cette protection. Nous vous recommandons d'activer cette option pour l'ensemble de votre code, car le code compilé sans cette option n'est pas protégé contre les attaques. Les vérifications de la protection du flux de contrôle impliquent un faible coût d'exécution, mais l'analyse du compilateur tente d'optimiser ces vérifications sur des liens indirects sécurisés.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez **Propriétés de configuration**, **C/C++**, **Génération de code**.

1. Sélectionnez la propriété **Protection du flux de contrôle** .

1. Dans la liste déroulante, choisissez **Oui** pour activer la protection du flux de contrôle ou **Non** pour la désactiver.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)