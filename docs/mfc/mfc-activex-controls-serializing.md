---
description: 'En savoir plus sur : contrôles ActiveX MFC : sérialisation'
title: 'Contrôles ActiveX MFC : sérialisation'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
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
ms.openlocfilehash: 24f49aa1dfb37c6ac981035f33d0f60e6fa398f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206043"
---
# <a name="mfc-activex-controls-serializing"></a>Contrôles ActiveX MFC : sérialisation

Cet article explique comment sérialiser un contrôle ActiveX. La sérialisation est le processus de lecture ou d’écriture sur un support de stockage persistant, tel qu’un fichier sur disque. La bibliothèque MFC (Microsoft Foundation Class) fournit une prise en charge intégrée de la sérialisation dans la classe `CObject` . `COleControl` étend cette prise en charge aux contrôles ActiveX à l’aide d’un mécanisme d’échange de propriétés.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

La sérialisation des contrôles ActiveX est implémentée en remplaçant [COleControl ::D opropexchange](reference/colecontrol-class.md#dopropexchange). Cette fonction, appelée pendant le chargement et l’enregistrement de l’objet de contrôle, stocke toutes les propriétés implémentées avec une variable membre ou une variable membre avec notification de modification.

Les rubriques suivantes abordent les principaux problèmes liés à la sérialisation d’un contrôle ActiveX :

- Implémentation `DoPropExchange` de la fonction pour sérialiser votre objet de contrôle

- [Personnalisation du processus de sérialisation](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implémentation de la prise en charge des versions](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a> Implémentation de la fonction DoPropExchange

Lorsque vous utilisez l’Assistant contrôle ActiveX pour générer le projet de contrôle, plusieurs fonctions de gestionnaire par défaut sont automatiquement ajoutées à la classe de contrôle, y compris l’implémentation par défaut de [COleControl ::D opropexchange](reference/colecontrol-class.md#dopropexchange). L’exemple suivant montre le code ajouté aux classes créées à l’aide de l’Assistant contrôle ActiveX :

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Si vous souhaitez rendre une propriété persistante, modifiez `DoPropExchange` en ajoutant un appel à la fonction d’échange de propriété. L’exemple suivant illustre la sérialisation d’une propriété CircleShape booléenne personnalisée, où la propriété CircleShape a la valeur par défaut **true**:

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

Le tableau suivant répertorie les fonctions d’échange de propriétés possibles que vous pouvez utiliser pour sérialiser les propriétés du contrôle :

|Fonctions d’échange de propriétés|Objectif|
|---------------------------------|-------------|
|**PX_Blob ()**|Sérialise une propriété de données de type binaire Large Object (BLOB).|
|**PX_Bool ()**|Sérialise une propriété de type Boolean.|
|**PX_Color ()**|Sérialise une propriété de couleur de type.|
|**PX_Currency ()**|Sérialise une propriété de type **CY** (Currency).|
|**PX_Double ()**|Sérialise une propriété de type **`double`** .|
|**PX_Font ()**|Sérialise une propriété de type font.|
|**PX_Float ()**|Sérialise une propriété de type **`float`** .|
|**PX_IUnknown ()**|Sérialise une propriété de type `LPUNKNOWN` .|
|**PX_Long ()**|Sérialise une propriété de type **`long`** .|
|**PX_Picture ()**|Sérialise une propriété d’image de type.|
|**PX_Short ()**|Sérialise une propriété de type **`short`** .|
|**PXstring( )**|Sérialise une propriété de type `CString` .|
|**PX_ULong ()**|Sérialise une propriété de type **ULong** .|
|**PX_UShort ()**|Sérialise une propriété de type **UShort** .|

Pour plus d’informations sur ces fonctions d’échange de propriétés, consultez [persistance des contrôles OLE](reference/persistence-of-ole-controls.md) dans la *référence MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Personnalisation du comportement par défaut de DoPropExchange

L’implémentation par défaut de `DoPropertyExchange` (comme indiqué dans la rubrique précédente) effectue un appel à la classe de base `COleControl` . Cela sérialise l’ensemble de propriétés prises en charge automatiquement par `COleControl` , qui utilise plus d’espace de stockage que la sérialisation des propriétés personnalisées du contrôle. La suppression de cet appel permet à votre objet de sérialiser uniquement les propriétés que vous considérez comme importantes. Les États de propriété stock que le contrôle a implémenté ne seront pas sérialisés lors de l’enregistrement ou du chargement de l’objet de contrôle, sauf si vous ajoutez explicitement **PX_** des appels pour eux.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a> Implémentation de la prise en charge des versions

La prise en charge des versions permet à un contrôle ActiveX révisé d’ajouter de nouvelles propriétés persistantes, tout en étant en mesure de détecter et de charger l’état persistant créé par une version antérieure du contrôle. Pour rendre la version d’un contrôle disponible dans le cadre de ses données persistantes, appelez [COleControl :: ExchangeVersion](reference/colecontrol-class.md#exchangeversion) dans la fonction du contrôle `DoPropExchange` . Cet appel est inséré automatiquement si le contrôle ActiveX a été créé à l’aide de l’Assistant contrôle ActiveX. Elle peut être supprimée si la prise en charge de version n’est pas nécessaire. Toutefois, le coût de la taille du contrôle est très faible (4 octets) pour la flexibilité ajoutée fournie par la prise en charge de la version.

Si le contrôle n’a pas été créé à l’aide de l’Assistant contrôle ActiveX, ajoutez un appel à `COleControl::ExchangeVersion` en insérant la ligne suivante au début de votre `DoPropExchange` fonction (avant l’appel à `COleControl::DoPropExchange` ) :

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Vous pouvez utiliser n’importe quelle **valeur DWORD** comme numéro de version. Les projets générés par l’Assistant contrôle ActiveX utilisent `_wVerMinor` et `_wVerMajor` comme valeur par défaut. Il s’agit des constantes globales définies dans le fichier d’implémentation de la classe de contrôle ActiveX du projet. Dans le reste de votre `DoPropExchange` fonction, vous pouvez appeler [CPropExchange :: GetVersion](reference/cpropexchange-class.md#getversion) à tout moment pour récupérer la version que vous enregistrez ou récupérez.

Dans l’exemple suivant, la version 1 de cet exemple de contrôle n’a qu’une propriété « Released ». La version 2 ajoute une propriété « OriginalDate ». Si le contrôle est chargé de charger l’état persistant à partir de l’ancienne version, il initialise la variable membre pour la nouvelle propriété à une valeur par défaut.

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Par défaut, un contrôle « convertit » les anciennes données au format le plus récent. Par exemple, si la version 2 d’un contrôle charge des données qui ont été enregistrées par la version 1, il écrit le format de la version 2 lorsqu’il est de nouveau enregistré. Si vous souhaitez que le contrôle enregistre les données au format dernière lecture, transmettez **false** en tant que troisième paramètre lors de l’appel de `ExchangeVersion` . Ce troisième paramètre est facultatif et a la **valeur true** par défaut.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](mfc-activex-controls.md)
