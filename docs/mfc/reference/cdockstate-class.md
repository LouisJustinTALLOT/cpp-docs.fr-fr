---
title: Cdockstate, classe
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
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262686"
---
# <a name="cdockstate-class"></a>Cdockstate, classe

Classe `CObject` sérialisée qui charge, décharge ou désactive l'état d'une ou de plusieurs barres de contrôles d'ancrage en mémoire persistante (un fichier).

## <a name="syntax"></a>Syntaxe

```
class CDockState : public CObject
```

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDockState::Clear](#clear)|Efface les informations d’état de station d’accueil.|
|[CDockState::GetVersion](#getversion)|Récupère le numéro de version de l’état de la barre.|
|[CDockState::LoadState](#loadstate)|Récupère des informations à partir du Registre d’état ou. Fichier INI.|
|[CDockState::SaveState](#savestate)|Enregistre les informations d’état dans le Registre ou le fichier INI.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|Tableau de pointeurs vers stocké les informations d’état avec une entrée pour chaque barre de contrôle d’ancrage.|

## <a name="remarks"></a>Notes

L’état d’ancrage inclut la taille et la position de la barre et si elle est ancrée. Lorsque la récupération stocké ancrer état, `CDockState` vérifie la barre position et, si la barre n’est pas visible avec les paramètres actuels de l’écran, `CDockState` met à l’échelle de la barre de positionner afin qu’il soit visible. L’objectif principal de `CDockState` consiste à conserver l’état complet d’un nombre de barres de contrôles et à autoriser cet état doit être enregistré et chargés dans du Registre, l’application. Fichier INI, ou sous forme binaire dans le cadre d’un `CArchive` contenu de l’objet.

La barre peut être n’importe quel contrôle de la barre, y compris une barre d’outils, la barre d’état ou la barre de boîte de dialogue. `CDockState` les objets sont écrites et lues vers ou à partir d’un fichier via un `CArchive` objet.

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) récupère les informations d’état de tous les frames de la fenêtre `CControlBar` les objets et les place dans le `CDockState` objet. Vous pouvez ensuite écrire le contenu de la `CDockState` objet vers le stockage avec [Serialize](../../mfc/reference/cobject-class.md#serialize) ou [CDockState::SaveState](#savestate). Si vous souhaitez ultérieurement restaurer l’état des barres de contrôle dans la fenêtre frame, vous pouvez charger l’état avec `Serialize` ou [CDockState::LoadState](#loadstate), puis utilisez [CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) pour appliquer l’enregistré état de barres de contrôles de la fenêtre frame.

Pour plus d’informations sur la station d’accueil de barres de contrôles, consultez les articles [barres de contrôles](../../mfc/control-bars.md), [barres d’outils : Ancrer et rendre flottantes](../../mfc/docking-and-floating-toolbars.md), et [Frame Windows](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Spécifications

**En-tête :** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

Appelez cette fonction pour effacer toutes les informations d’ancrage stockées dans le `CDockState` objet.

```
void Clear();
```

### <a name="remarks"></a>Notes

Cela inclut non seulement si la barre est ancrée ou non, mais la taille et la position de la barre et si elle est visible ou non.

##  <a name="getversion"></a>  CDockState::GetVersion

Appelez cette fonction pour récupérer le numéro de version de l’état de la barre.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valeur de retour

1 si la barre stockée informations sont antérieures à actuel de la barre d’état ; 2 si la barre stockée informations sont le même que l’actuel barre d’état.

### <a name="remarks"></a>Notes

Prise en charge de la version permet une barre révisée ajouter de nouvelles propriétés persistantes et toujours être en mesure de détecter et charger l’état persistant créé par une version antérieure de la barre.

##  <a name="loadstate"></a>  CDockState::LoadState

Appelez cette fonction pour récupérer des informations d’état à partir du Registre ou. Fichier INI.

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Pointe vers une chaîne null-teminated qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le Registre Windows où sont stockées les informations d’état.

### <a name="remarks"></a>Notes

Le nom du profil est la section de l’application. Fichier INI ou du Registre qui contient les informations d’état des barres. Vous pouvez enregistrer le contrôle barre d’informations d’état dans le Registre ou. Fichier INI avec `SaveState`.

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

Un `CPtrArray` objet qui est un tableau de pointeurs vers les informations de barre de contrôle stockée pour chaque barre de contrôle qui a enregistré des informations d’état dans le `CDockState` objet.

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

Appelez cette fonction pour enregistrer les informations d’état dans le Registre ou. Fichier INI.

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Pointe vers une chaîne null-teminated qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le Registre Windows où sont stockées les informations d’état.

### <a name="remarks"></a>Notes

Le nom du profil est la section de l’application. Fichier INI ou du Registre qui contient les informations d’état de la barre de contrôle. `SaveState` enregistre également la taille d’écran actuelle. Vous pouvez récupérer des informations de barre de contrôle à partir du Registre ou. Fichier INI avec `LoadState`.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
