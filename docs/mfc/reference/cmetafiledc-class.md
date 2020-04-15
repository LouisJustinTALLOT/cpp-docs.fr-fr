---
title: Classe CMetaFileDC
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369952"
---
# <a name="cmetafiledc-class"></a>Classe CMetaFileDC

Implémente un métafichier Windows, qui contient une séquence de commandes SQL GDI (Graphics Device Interface) que vous pouvez relire pour créer une image ou du texte voulu.

## <a name="syntax"></a>Syntaxe

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Construit un objet `CMetaFileDC`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CMetaFileDC::Fermer](#close)|Ferme le contexte de l’appareil et crée une poignée métadilienne.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Ferme un contexte d’appareil amélioré et crée une poignée améliorée-metafile.|
|[CMetaFileDC::Créer](#create)|Crée le contexte de l’appareil métadilile Windows et le fixe à l’objet. `CMetaFileDC`|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crée un contexte d’appareil métaafile pour un métaafile format amélioré.|

## <a name="remarks"></a>Notes

Pour implémenter un métaafile Windows, créez d’abord un `CMetaFileDC` objet. Invoquez le `CMetaFileDC` constructeur, puis appelez la fonction membre [Create,](#create) qui crée `CMetaFileDC` un contexte d’appareil métadique Windows et l’attache à l’objet.

Ensuite, `CMetaFileDC` envoyez à l’objet la séquence des commandes DE CDC GDI que vous avez l’intention de rejouer. Seules les commandes GDI qui créent `MoveTo` `LineTo`des sorties, telles que et, peuvent être utilisées.

Après avoir envoyé les commandes souhaitées au metafile, appelez la `Close` fonction membre, qui ferme les contextes de périphériques métaafiles et renvoie une poignée métaafile. Ensuite, disposez de l’objet. `CMetaFileDC`

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) peut alors utiliser la poignée metafile pour jouer le metafile à plusieurs reprises. Le metafile peut également être manipulé par des fonctions Windows telles que [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), qui copie un métaafile au disque.

Lorsque le métaafile n’est plus nécessaire, supprimez-le de la mémoire avec la fonction [Windows DeleteMetaFile.](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)

Vous pouvez également `CMetaFileDC` implémenter l’objet afin qu’il `GetTextExtent`puisse gérer à la fois les appels de sortie et attribuer des appels GDI tels que . Un tel métaafile est plus flexible et peut plus facilement réutiliser le code GDI général, qui se compose souvent d’un mélange d’appels de sortie et d’attribut. La `CMetaFileDC` classe hérite de `m_hDC` deux `m_hAttribDC`contextes d’appareils, et , de CDC. Le `m_hDC` contexte de l’appareil gère tous `m_hAttribDC` les appels de sortie [CDC](../../mfc/reference/cdc-class.md) GDI et le contexte de l’appareil gère tous les appels d’attributs CDC GDI. Normalement, ces deux contextes d’appareil se réfèrent au même appareil. Dans le `CMetaFileDC`cas de , l’attribut DC est configuré à NULL par défaut.

Créez un deuxième contexte de périphérique qui indique l’écran, une imprimante ou `SetAttribDC` un appareil autre qu’un métaafile, puis appelez la fonction membre pour associer le nouveau contexte de périphérique avec `m_hAttribDC`. Les appels d’information de GDI `m_hAttribDC`seront désormais adressés au nouveau . Les appels de sortie `m_hDC`GDI iront à , qui représente le metafile.

Pour plus `CMetaFileDC`d’informations sur , voir [Contextes périphériques](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Spécifications

**En-tête:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Fermer

Ferme le contexte de l’appareil métaafile et crée une poignée métaafile Windows qui peut être utilisée pour jouer le métaafile en utilisant la fonction de membre [CDC::PlayMetaFile.](../../mfc/reference/cdc-class.md#playmetafile)

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valeur de retour

Un HMETAFILE valide si la fonction est réussie; autrement NULL.

### <a name="remarks"></a>Notes

La poignée metafile Windows peut également être utilisée pour manipuler le métaafile avec des fonctions Windows telles que [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Supprimer le métaafile après utilisation en appelant la fonction Windows [DeleteMetaFile.](/windows/win32/api/wingdi/nf-wingdi-deletemetafile)

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced

Ferme un contexte d’appareil amélioré et renvoie une poignée qui identifie un métaafile format amélioré.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valeur de retour

Une poignée d’un metafile amélioré, en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Une application peut utiliser la poignée améliorée-metafile retournée par cette fonction pour effectuer les tâches suivantes :

- Afficher une image stockée dans un métaafile amélioré

- Créez des copies du metafile amélioré

- Énumérer, modifier ou copier des enregistrements individuels dans le metafile amélioré

- Récupérer une description facultative du contenu metafile de l’en-tête amélioré

- Récupérer une copie de l’en-tête amélioré-metafile

- Récupérer une copie binaire du metafile amélioré

- Énumérer les couleurs dans la palette facultative

- Convertir un métaafile format amélioré en un métaafile format Windows

Lorsque l’application n’a plus besoin de la poignée metafile `DeleteEnhMetaFile` améliorée, elle doit libérer la poignée en appelant la fonction Win32.

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC

Construire `CMetaFileDC` un objet en deux étapes.

```
CMetaFileDC();
```

### <a name="remarks"></a>Notes

Tout d’abord, appelez, `CMetaFileDC`puis appelez `Create`, qui crée le `CMetaFileDC` contexte de périphérique Windows metafile et le fixe à l’objet.

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Créer

Construire `CMetaFileDC` un objet en deux étapes.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFilename*<br/>
Points à une chaîne de caractères non terminée. Spécifie le nom de fichier du metafile à créer. Si *lpszFilename* est NULL, un nouveau metafile en mémoire est créé.

### <a name="return-value"></a>Valeur de retour

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Tout d’abord, `CMetaFileDC`appelez `Create`le constructeur, puis appelez , qui crée le `CMetaFileDC` contexte de l’appareil windows metafile et le fixe à l’objet.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced

Crée un contexte d’appareil pour un métaafile format amélioré.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Paramètres

*pDCRef (en)*<br/>
Identifie un dispositif de référence pour le métaafile amélioré.

*lpszFileName*<br/>
Points à une chaîne de caractères non terminée. Spécifie le nom de fichier pour le metafile amélioré à créer. Si ce paramètre est NULL, le métafaisile amélioré est basé sur la `DeleteEnhMetaFile` mémoire et son contenu perdu lorsque l’objet est détruit ou lorsque la fonction Win32 est appelée.

*lpBounds (lpBounds)*<br/>
Indique une structure de données [RECT](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie les dimensions des unités HIMETRIC (par tranches de 0,01 millimètre) de l’image à stocker dans le métadafile amélioré.

*lpszDescription*<br/>
Points à une chaîne zéro-ended qui spécifie le nom de l’application qui a créé l’image, ainsi que le titre de l’image.

### <a name="return-value"></a>Valeur de retour

Une poignée du contexte de l’appareil pour le metafile amélioré, en cas de succès; autrement NULL.

### <a name="remarks"></a>Notes

Ce DC peut être utilisé pour stocker une image indépendante de l’appareil.

Windows utilise le dispositif de référence identifié par le paramètre *pDCRef* pour enregistrer la résolution et les unités de l’appareil sur lequel une image est apparue à l’origine. Si le *paramètre pDCRef* est NULL, il utilise le dispositif d’affichage actuel pour référence.

Les membres gauches `RECT` et supérieurs de la structure de données indiqués par le paramètre *lpBounds* doivent être plus petits que les membres droits et inférieurs, respectivement. Les points le long des bords du rectangle sont inclus dans l’image. Si *lpBounds* est NULL, l’interface de périphérique graphique (GDI) calcule les dimensions du plus petit rectangle qui peut enfermer l’image dessinée par l’application. Le *paramètre lpBounds* doit être fourni dans la mesure du possible.

La chaîne indiquée par le paramètre *lpszDescription* doit contenir un caractère nul entre le nom de l’application et le nom de l’image et doit se terminer avec deux caractères nuls — par exemple, « XYZ Graphics Editor -0Bald Eagle -0 », où le numéro 0 représente le caractère nul. Si *lpszDescription* est NULL, il n’y a pas d’entrée correspondante dans l’en-tête amélioré-metafile.

Les applications utilisent le DC créé par cette fonction pour stocker une image graphique dans un métaafile amélioré. La poignée identifiant ce DC peut être transmise à n’importe quelle fonction GDI.

Après qu’une application stocke une image dans un métaafile amélioré, `CDC::PlayMetaFile` elle peut afficher l’image sur n’importe quel périphérique de sortie en appelant la fonction. Lors de l’affichage de l’image, Windows utilise le rectangle pointé vers le paramètre *lpBounds* et les données de résolution de l’appareil de référence pour positionner et mettre l’image à l’échelle. Le contexte de l’appareil retourné par cette fonction contient les mêmes attributs par défaut associés à n’importe quel nouveau DC.

Les applications doivent utiliser `GetWinMetaFileBits` la fonction Win32 pour convertir un métaafile amélioré à l’ancien format métadique Windows.

Le nom de fichier pour le metafile amélioré devrait utiliser le . Extension EMF.

## <a name="see-also"></a>Voir aussi

[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
