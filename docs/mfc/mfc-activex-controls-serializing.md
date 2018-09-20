---
title: 'Contrôles ActiveX MFC : Sérialisation | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3be523feaacb403076f2c066943ca55ace958dce
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401835"
---
# <a name="mfc-activex-controls-serializing"></a>Contrôles ActiveX MFC : sérialisation

Cet article décrit comment sérialiser un contrôle ActiveX. Sérialisation est le processus de lecture ou écriture sur un support de stockage persistant, tel qu’un fichier de disque. La bibliothèque Microsoft Foundation classes (MFC) fournit la prise en charge intégrée pour la sérialisation dans la classe `CObject`. `COleControl` étend cette prise en charge pour les contrôles ActiveX via l’utilisation d’un mécanisme d’échange de propriété.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent les ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Sérialisation pour les contrôles ActiveX est implémentée en substituant [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Cette fonction, appelée pendant le chargement et l’enregistrement de l’objet contrôle, stocke toutes les propriétés implémentées avec une variable de membre ou une variable membre avec notification de modification.

Les rubriques suivantes couvrent les principaux problèmes liés à la sérialisation d’un contrôle ActiveX :

- Implémentation `DoPropExchange` pour sérialiser un objet contrôle (fonction)

- [Personnalisation du processus de sérialisation](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implémentation des versions prises en charge](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> Implémentation de la fonction DoPropExchange

Lorsque vous utilisez l’Assistant contrôle ActiveX pour générer le projet de contrôle, plusieurs fonctions de gestionnaire par défaut sont automatiquement ajoutées à la classe de contrôle, y compris l’implémentation par défaut de [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). L’exemple suivant montre le code ajouté aux classes créées par l’Assistant contrôle ActiveX :

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Si vous souhaitez rendre une propriété persistante, modifiez `DoPropExchange` en ajoutant un appel à la fonction d’échange de propriété. L’exemple suivant illustre la sérialisation d’une propriété booléenne personnalisée CircleShape, où la propriété CircleShape a la valeur par défaut **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

Le tableau suivant répertorie les fonctions d’échange de propriété possibles que vous pouvez utiliser pour sérialiser les propriétés du contrôle :

|Fonctions d’échange de propriété|Objectif|
|---------------------------------|-------------|
|**() PX_Blob**|Sérialise un type de propriété de données d’objet binaire volumineux (BLOB).|
|**() PX_Bool**|Sérialise un type de propriété booléenne.|
|**() PX_Color**|Sérialise une propriété de couleur de type.|
|**() PX_Currency**|Sérialise un type **CY** propriété de (devise).|
|**() PX_Double**|Sérialise un type **double** propriété.|
|**() PX_Font**|Sérialise une propriété de type de police.|
|**() PX_Float**|Sérialise un type **float** propriété.|
|**() PX_IUnknown**|Sérialise une propriété de type `LPUNKNOWN`.|
|**() PX_Long**|Sérialise un type **long** propriété.|
|**() PX_Picture**|Sérialise une propriété de type Picture.|
|**() PX_Short**|Sérialise un type **court** propriété.|
|**() PXstring**|Sérialise un type `CString` propriété.|
|**() PX_ULong**|Sérialise un type **ULONG** propriété.|
|**() PX_UShort**|Sérialise un type **USHORT** propriété.|

Pour plus d’informations sur ces fonctions d’échange de propriété, consultez [persistance des contrôles OLE](../mfc/reference/persistence-of-ole-controls.md) dans le *référence MFC*.

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Personnalisation du comportement par défaut de DoPropExchange

L’implémentation par défaut de `DoPropertyExchange` (comme indiqué dans la rubrique précédente) effectue un appel à la classe de base `COleControl`. Il sérialise le jeu de propriétés automatiquement pris en charge par `COleControl`, qui utilise l’espace de stockage à sérialiser uniquement les propriétés personnalisées du contrôle. Suppression de cet appel permet à votre objet à sérialiser uniquement les propriétés que vous jugez importante. Tout le contrôle a implémenté les États de propriétés stock ne seront pas sérialisés lors de l’enregistrement ou le chargement de l’objet de contrôle, sauf si vous ajoutez explicitement **PX_** appelle pour eux.

##  <a name="_core_implementing_version_support"></a> Implémentation des versions prises en charge

Prise en charge de la version permet un contrôle ActiveX révisé ajouter de nouvelles propriétés persistantes et toujours être en mesure de détecter et charger l’état persistant créé par une version antérieure du contrôle. Pour rendre une version du contrôle disponible dans le cadre de ses données persistantes, appelez [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) dans le contrôle `DoPropExchange` (fonction). Cet appel est inséré automatiquement si le contrôle ActiveX a été créé à l’aide de l’Assistant contrôle ActiveX. Il peut être supprimé si la prise en charge de la version n’est pas nécessaire. Toutefois, le coût de la taille du contrôle est très petite (4 octets) pour la flexibilité accrue qui fournit des versions prises en charge.

Si le contrôle n’a pas créé avec l’Assistant contrôle ActiveX, ajoutez un appel à `COleControl::ExchangeVersion` en insérant la ligne suivante au début de votre `DoPropExchange` (fonction) (avant l’appel à `COleControl::DoPropExchange`) :

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Vous pouvez utiliser les **DWORD** en tant que le numéro de version. Utilisent des projets générés par l’Assistant contrôle ActiveX `_wVerMinor` et `_wVerMajor` en tant que la valeur par défaut. Il s’agit de constantes globales définies dans le fichier d’implémentation de classe de contrôle ActiveX du projet. Dans le reste de votre `DoPropExchange` (fonction), vous pouvez appeler [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) à tout moment pour récupérer la version que vous enregistrez ou récupération.

Dans l’exemple suivant, la version 1 de cet exemple de contrôle a uniquement une propriété « ReleaseDate ». Version 2 ajoute une propriété « OriginalDate ». Si le contrôle est demandé pour charger l’état persistant de l’ancienne version, il initialise la variable membre pour la nouvelle propriété à une valeur par défaut.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Par défaut, un contrôle « convertit « anciennes données pour le format le plus récent. Par exemple, si la version 2 d’un contrôle charge des données qui ont été enregistrées par la version 1, il écrit le format de version 2 lorsqu’elle est enregistrée à nouveau. Si vous souhaitez que le contrôle pour enregistrer les données dans la format de dernière lecture, passer **FALSE** en tant que troisième paramètre lors de l’appel `ExchangeVersion`. Cet troisième paramètre est facultatif et est **TRUE** par défaut.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

