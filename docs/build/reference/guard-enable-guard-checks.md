---
description: En savoir plus sur:/GUARD (activer les vérifications de protection)
title: /GUARD (activer les contrôles de protection)
ms.date: 11/04/2016
ms.assetid: 72758e23-70ac-4616-94d7-d767477406d1
ms.openlocfilehash: 4f76de815bc10f8e1203510b25b237fe8db93444
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97191717"
---
# <a name="guard-enable-guard-checks"></a>/GUARD (activer les contrôles de protection)

Spécifie la prise en charge pour les contrôles de protection du flux de contrôle de l'image exécutable.

## <a name="syntax"></a>Syntaxe

```
/GUARD:{CF|NO}
```

## <a name="remarks"></a>Notes

Quand /GUARD:CF est spécifié, l'éditeur de liens modifie l'en-tête d'un fichier .dll ou .exe pour indiquer la prise en charge des contrôles d'exécution de la protection du flux de contrôle (CFG). L'éditeur de liens ajoute également les données d'adresse cible du flux de contrôle nécessaire dans l'en-tête. Par défaut, /GUARD:CF est désactivé. Il peut être désactivé explicitement en spécifiant /GUARD:NO. Pour être efficace,/GUARD : CF requiert également l’option de l’éditeur de liens [/DynamicBase (utiliser la randomisation du format d’espace d’adresse)](dynamicbase-use-address-space-layout-randomization.md) , qui est activée par défaut.

Lorsque le code source est compilé à l’aide de l’option [/Guard : cf](guard-enable-control-flow-guard.md) , le compilateur analyse le workflow en examinant tous les appels indirects pour les adresses cibles possibles. Le compilateur insère le code pour vérifier que l'adresse cible d'une instruction d'appel indirect figure dans la liste des adresses cibles connues au moment de l'exécution. Les systèmes d'exploitation qui prennent en charge la protection CFG arrêtent tout programme qui ne satisfait pas une vérification à l'exécution CFG. Il est ainsi plus difficile pour un attaquant d'exécuter du code malveillant en recourant à une altération des données pour modifier une cible d'appel.

L'option /GUARD:CF doit être spécifiée dans le compilateur et l'éditeur de liens pour créer des images exécutables avec protection CFG. Le code qui est compilé, mais pas lié avec l'option /GUARD:CF implique un coût de vérifications à l'exécution, mais n'active pas la protection CFG. Lorsque l’option/GUARD : CF est spécifiée à la `cl` commande pour compiler et lier en une seule étape, le compilateur passe l’indicateur à l’éditeur de liens. Quand la propriété de **protection du workflow de contrôle** est définie dans Visual Studio, l’option/Guard : CF est passée au compilateur et à l’éditeur de liens. Lorsque des fichiers objets ou des bibliothèques ont été compilés séparément, l’option doit être explicitement spécifiée dans la `link` commande.

### <a name="to-set-this-linker-option-in-visual-studio"></a>Pour définir cette option d'éditeur de liens dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez **Propriétés de configuration**, **éditeur de liens**, ligne de **commande**.

1. Dans **options supplémentaires**, entrez `/GUARD:CF` .

## <a name="see-also"></a>Voir aussi

[/guard (Activer la protection du flux de contrôle)](guard-enable-control-flow-guard.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
