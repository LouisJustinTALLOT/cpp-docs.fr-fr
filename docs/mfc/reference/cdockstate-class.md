---
title: CDockState, classe
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 9850486407ee7550ee866a10e656d45ad18fc196
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753260"
---
# <a name="cdockstate-class"></a>CDockState, classe

Classe `CObject` sérialisée qui charge, décharge ou désactive l'état d'une ou de plusieurs barres de contrôles d'ancrage en mémoire persistante (un fichier).

## <a name="syntax"></a>Syntaxe

```
class CDockState : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockState::Clair](#clear)|Efface les informations sur l’état du quai.|
|[CDockState::GetVersion](#getversion)|Récupère le numéro de version de l’état de la barre stockée.|
|[CDockState::LoadState](#loadstate)|Récupère les informations d’état du registre ou . Fichier INI.|
|[CDockState::SaveState](#savestate)|Enregistre les informations de l’État au registre ou au fichier INI.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Array de pointeurs à l’information stockée d’état de dock avec une entrée pour chaque barre de commande.|

## <a name="remarks"></a>Notes

L’état du quai comprend la taille et la position du bar et si oui ou non il est amarré. Lors de la récupération de `CDockState` l’état du quai stocké, vérifie la position de la `CDockState` barre et, si la barre n’est pas visible avec les paramètres actuels de l’écran, balance la position de la barre de sorte qu’elle soit visible. L’objectif `CDockState` principal est de tenir l’état entier d’un certain nombre de barres de contrôle et de permettre à cet état d’être enregistré et chargé soit au registre, la demande . Fichier INI, ou sous forme `CArchive` binaire dans le cadre du contenu d’un objet.

La barre peut être n’importe quelle barre de commande amarable, y compris une barre d’outils, une barre d’état ou une barre de dialogue. `CDockState`objets sont écrits et lus `CArchive` à un fichier ou à partir d’un objet.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) récupère les informations d’état de `CControlBar` tous les objets `CDockState` de la fenêtre du cadre et les met dans l’objet. Vous pouvez ensuite écrire `CDockState` le contenu de l’objet au stockage avec [Serialize](../../mfc/reference/cobject-class.md#serialize) ou [CDockState:SaveState](#savestate). Si vous souhaitez plus tard restaurer l’état des barres de contrôle `Serialize` dans la fenêtre du cadre, vous pouvez charger l’état avec ou [CDockState::LoadState](#loadstate), puis utilisez [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) pour appliquer l’état enregistré aux barres de contrôle de la fenêtre de cadre.

Pour plus d’informations sur les barres de contrôle d’amarrage, voir les articles [Control Bars](../../mfc/control-bars.md), [Toolbars: Docking and Floating](../../mfc/docking-and-floating-toolbars.md), et Frame [Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Spécifications

**En-tête:** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState::Clair

Appelez cette fonction pour effacer toutes `CDockState` les informations d’amarrage stockées dans l’objet.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Cela comprend non seulement si la barre est amarré ou non, mais la taille et la position de la barre et si oui ou non il est visible.

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState::GetVersion

Appelez cette fonction pour récupérer le numéro de version de l’état de la barre stockée.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valeur de retour

1 si les informations de barre stockées sont plus anciennes que l’état actuel de barre; 2 si les informations de barre stockées sont les mêmes que l’état actuel de barre.

### <a name="remarks"></a>Notes

Le support de version permet à une barre révisée d’ajouter de nouvelles propriétés persistantes tout en étant en mesure de détecter et de charger l’état persistant créé par une version antérieure de la barre.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState::LoadState

Appelez cette fonction pour récupérer les informations de l’État du registre ou . Fichier INI.

```cpp
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Indique une chaîne non-téméritée qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le registre Windows où les informations de l’État sont stockées.

### <a name="remarks"></a>Notes

Le nom de profil est la section de l’application . Fichier INI ou le registre qui contient les informations d’état des barres. Vous pouvez enregistrer les informations d’état de barre de contrôle au registre ou . Fichier INI `SaveState`avec .

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>CDockState::m_arrBarInfo

Un `CPtrArray` objet qui est un tableau de pointeurs aux informations de barre de `CDockState` contrôle stockées pour chaque barre de contrôle qui a enregistré des informations d’état dans l’objet.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState::SaveState

Appelez cette fonction pour enregistrer les informations de l’État au registre ou . Fichier INI.

```cpp
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Indique une chaîne non-téméritée qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le registre Windows où les informations de l’État sont stockées.

### <a name="remarks"></a>Notes

Le nom de profil est la section de l’application . Fichier INI ou le registre qui contient les informations d’état de la barre de contrôle. `SaveState`enregistre également la taille actuelle de l’écran. Vous pouvez récupérer des informations de barre de contrôle du registre ou . Fichier INI `LoadState`avec .

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
