---
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
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364554"
---
# <a name="mfc-activex-controls-serializing"></a>Contrôles ActiveX MFC : sérialisation

Cet article traite de la façon de sérialiser un contrôle ActiveX. La sérialisation est le processus de lecture ou d’écriture à un support de stockage persistant, comme un fichier disque. La bibliothèque Microsoft Foundation Class (MFC) fournit un `CObject`support intégré pour la sérialisation en classe . `COleControl`étend ce support aux contrôles ActiveX grâce à l’utilisation d’un mécanisme d’échange de biens.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

La sérialisation des contrôles ActiveX est mise en œuvre en supprimant [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Cette fonction, appelée lors du chargement et de l’enregistrement de l’objet de commande, stocke toutes les propriétés implémentées avec une variable de membre ou une variable de membre avec notification de modification.

Les sujets suivants couvrent les principaux enjeux liés à la sérialisation d’un contrôle ActiveX :

- Fonction `DoPropExchange` de mise en œuvre pour sérialiser votre objet de contrôle

- [Personnaliser le processus de sérialisation](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Mise en œuvre du support de version](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Mise en œuvre de la fonction DoPropExchange

Lorsque vous utilisez l’Assistant de Contrôle ActiveX pour générer le projet de contrôle, plusieurs fonctions de gestionnaire par défaut sont automatiquement ajoutées à la classe de contrôle, y compris la mise en œuvre par défaut de [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). L’exemple suivant montre le code ajouté aux classes créées avec l’Assistant de Contrôle ActiveX :

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Si vous voulez rendre une `DoPropExchange` propriété persistante, modifiez en ajoutant un appel à la fonction d’échange de propriété. L’exemple suivant démontre la sérialisation d’une propriété Boolean CircleShape personnalisée, où la propriété CircleShape a une valeur par défaut de **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

Le tableau suivant répertorie les fonctions possibles d’échange de propriété que vous pouvez utiliser pour sérialiser les propriétés du contrôle :

|Fonctions d’échange de propriété|Objectif|
|---------------------------------|-------------|
|**PX_Blob)**|Sérialise une propriété de données binaires à grand objet (BLOB).|
|**PX_Bool)**|Sérialise une propriété Boolean de type.|
|**PX_Color)**|Sérialise une propriété de couleur type.|
|**PX_Currency)**|Sérialise une propriété de type **CY** (monnaie).|
|**PX_Double)**|Sérialise une **double** propriété de type.|
|**PX_Font)**|Sérialise une propriété de type Font.|
|**PX_Float)**|Sérialise une propriété **flottante** type.|
|**PX_IUnknown)**|Sérialise une `LPUNKNOWN`propriété de type .|
|**PX_Long)**|Sérialise une propriété **longue** de type.|
|**PX_Picture)**|Sérialise une propriété d’image de type.|
|**PX_Short)**|Sérialise une propriété **courte** de type.|
|**PXstring( )**|Sérialise `CString` une propriété type.|
|**PX_ULong)**|Sérialise une propriété **ULONG** de type.|
|**PX_UShort)**|Sérialise une propriété **USHORT** de type.|

Pour plus d’informations sur ces fonctions d’échange de biens, voir [Persistence of OLE Controls](../mfc/reference/persistence-of-ole-controls.md) in the *MFC Reference*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Personnaliser le comportement par défaut de DoPropExchange

La mise `DoPropertyExchange` en œuvre par défaut de (comme `COleControl`indiqué dans le sujet précédent) fait un appel à la classe de base . Ceci sérialisse l’ensemble `COleControl`de propriétés automatiquement pris en charge par , qui utilise plus d’espace de stockage que la sérialisation uniquement les propriétés personnalisées du contrôle. La suppression de cet appel permet à votre objet de sérialiser uniquement les propriétés que vous jugez importantes. Toute propriété stock stipule que le contrôle a mis en œuvre ne sera pas sérialisé lors de l’enregistrement ou le chargement de l’objet de commande à moins que vous ajoutez explicitement **PX_** appels pour eux.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Mise en œuvre du support de version

Le support de version permet à un contrôle ActiveX révisé d’ajouter de nouvelles propriétés persistantes, tout en étant en mesure de détecter et de charger l’état persistant créé par une version antérieure du contrôle. Pour rendre la version d’un contrôle disponible dans le cadre de ses données persistantes, appelez [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) dans la fonction du `DoPropExchange` contrôle. Cet appel est automatiquement inséré si le contrôle ActiveX a été créé à l’aide de l’Assistant de Contrôle ActiveX. Il peut être supprimé si le support de la version n’est pas nécessaire. Cependant, le coût de la taille du contrôle est très faible (4 octets) pour la flexibilité supplémentaire que le support de version fournit.

Si le contrôle n’a pas été créé avec `COleControl::ExchangeVersion` l’Assistant de Contrôle ActiveX, ajoutez un appel en insérant la ligne suivante au début de votre `DoPropExchange` fonction (avant l’appel à `COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Vous pouvez utiliser n’importe quel **DWORD** comme numéro de version. Projets générés par l’utilisation `_wVerMinor` ActiveX Control Wizard et `_wVerMajor` par défaut. Il s’agit de constantes globales définies dans le fichier de mise en œuvre de la classe de contrôle ActiveX du projet. Dans le reste `DoPropExchange` de votre fonction, vous pouvez appeler [CPropExchange:GetVersion](../mfc/reference/cpropexchange-class.md#getversion) à tout moment pour récupérer la version que vous enregistrez ou récupérez.

Dans l’exemple suivant, la version 1 de ce contrôle de l’échantillon n’a qu’une propriété "ReleaseDate". La version 2 ajoute une propriété "OriginalDate". Si le contrôle est chargé de charger l’état persistant de l’ancienne version, il initialise la variable du membre pour la nouvelle propriété à une valeur par défaut.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Par défaut, un contrôle "convertit" les anciennes données au dernier format. Par exemple, si la version 2 d’un contrôle charge les données qui ont été enregistrées par la version 1, elle écrira le format de la version 2 lorsqu’elle sera de nouveau enregistrée. Si vous voulez que le contrôle enregistre les **FALSE** données dans le format `ExchangeVersion`la dernière lecture, passez FALSE comme un troisième paramètre lors de l’appel . Ce troisième paramètre est facultatif et est **VRAI** par défaut.

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
