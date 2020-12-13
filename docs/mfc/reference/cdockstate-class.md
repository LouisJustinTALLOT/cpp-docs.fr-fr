---
description: 'En savoir plus sur : classe CDockState'
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
ms.openlocfilehash: 4bdc17ec5a09b812609b8aa71e3f361603c1106f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184957"
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
|[CDockState :: Clear](#clear)|Efface les informations d’état d’ancrage.|
|[CDockState :: GetVersion](#getversion)|Récupère le numéro de version de l’état de la barre stockée.|
|[CDockState :: LoadState](#loadstate)|Récupère des informations d’État à partir du registre ou. Fichier INI.|
|[CDockState :: saveste](#savestate)|Enregistre les informations d’État dans le registre ou le fichier INI.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDockState :: m_arrBarInfo](#m_arrbarinfo)|Tableau de pointeurs vers les informations d’état d’ancrage stockées avec une entrée pour chaque barre de contrôle.|

## <a name="remarks"></a>Notes

L’état d’ancrage comprend la taille et la position de la barre et indique si elle est ancrée ou non. Lors de la récupération de l’état d’ancrage stocké, `CDockState` vérifie la position de la barre et, si la barre n’est pas visible avec les paramètres de l’écran actuel, `CDockState` met à l’échelle la position de la barre afin qu’elle soit visible. L’objectif principal de `CDockState` consiste à conserver l’intégralité de l’état d’un certain nombre de barres de contrôles et à autoriser l’enregistrement et le chargement de cet État dans le registre, l’application. Fichier INI ou sous forme binaire dans le cadre du contenu d’un `CArchive` objet.

La barre peut être n’importe quelle barre de contrôle Ancrable, y compris une barre d’outils, une barre d’État ou une barre de boîte de dialogue. `CDockState` les objets sont écrits et lus vers ou à partir d’un fichier via un `CArchive` objet.

[CFrameWnd :: GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate) récupère les informations d’état de tous les objets de la fenêtre frame `CControlBar` et les place dans l' `CDockState` objet. Vous pouvez ensuite écrire le contenu de l' `CDockState` objet dans le stockage avec [Serialize](../../mfc/reference/cobject-class.md#serialize) ou [CDockState :: saveste](#savestate). Si, par la suite, vous souhaitez restaurer l’état des barres de contrôles dans la fenêtre frame, vous pouvez charger l’état avec `Serialize` ou [CDockState :: LoadState](#loadstate), puis utiliser [CFrameWnd :: SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate) pour appliquer l’état enregistré aux barres de contrôle de la fenêtre frame.

Pour plus d’informations sur l’ancrage des barres de contrôles, consultez les articles [barres de contrôles](../../mfc/control-bars.md), barres [d’outils : ancrage et flottant](../../mfc/docking-and-floating-toolbars.md), et [fenêtres Frame](../../mfc/frame-windows.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>Spécifications

**En-tête :** afxadv. h

## <a name="cdockstateclear"></a><a name="clear"></a> CDockState :: Clear

Appelez cette fonction pour effacer toutes les informations d’ancrage stockées dans l' `CDockState` objet.

```cpp
void Clear();
```

### <a name="remarks"></a>Notes

Cela comprend non seulement si la barre est ancrée ou non, mais aussi la taille et la position de la barre et si elle est visible ou non.

## <a name="cdockstategetversion"></a><a name="getversion"></a> CDockState :: GetVersion

Appelez cette fonction pour récupérer le numéro de version de l’état de la barre stockée.

```
DWORD GetVersion();
```

### <a name="return-value"></a>Valeur renvoyée

1 si les informations de la barre stockée sont antérieures à l’état de la barre actuelle ; 2 si les informations de la barre stockée sont identiques à l’état de la barre actuelle.

### <a name="remarks"></a>Notes

La prise en charge des versions permet à une barre modifiée d’ajouter de nouvelles propriétés persistantes tout en étant en mesure de détecter et de charger l’état persistant créé par une version antérieure de la barre.

## <a name="cdockstateloadstate"></a><a name="loadstate"></a> CDockState :: LoadState

Appelez cette fonction pour récupérer des informations d’État à partir du registre ou. Fichier INI.

```cpp
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Pointe vers une chaîne de teminated null qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le Registre Windows où les informations d’État sont stockées.

### <a name="remarks"></a>Notes

Le nom du profil est la section de l’application. Fichier INI ou registre qui contient les informations d’état des barres. Vous pouvez enregistrer les informations d’état de la barre de contrôle dans le registre ou. Fichier INI avec `SaveState` .

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a> CDockState :: m_arrBarInfo

`CPtrArray`Objet qui est un tableau de pointeurs vers les informations de barre de contrôles stockées pour chaque barre de contrôle qui a enregistré des informations d’État dans l' `CDockState` objet.

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a> CDockState :: saveste

Appelez cette fonction pour enregistrer les informations d’État dans le registre ou. Fichier INI.

```cpp
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>Paramètres

*lpszProfileName*<br/>
Pointe vers une chaîne de teminated null qui spécifie le nom d’une section dans le fichier d’initialisation ou une clé dans le Registre Windows où les informations d’État sont stockées.

### <a name="remarks"></a>Notes

Le nom du profil est la section de l’application. Fichier INI ou registre qui contient les informations d’état de la barre de contrôle. `SaveState` enregistre également la taille actuelle de l’écran. Vous pouvez récupérer des informations sur la barre de contrôle à partir du registre ou. Fichier INI avec `LoadState` .

## <a name="see-also"></a>Voir aussi

[CObject (classe)](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
