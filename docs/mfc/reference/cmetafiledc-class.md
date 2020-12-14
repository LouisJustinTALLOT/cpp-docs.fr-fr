---
description: 'En savoir plus sur : classe CMetaFileDC'
title: CMetaFileDC, classe
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
ms.openlocfilehash: b4b506818b1864c40225055faa2582820f15f423
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336623"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC, classe

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
|[CMetaFileDC :: Close](#close)|Ferme le contexte de périphérique et crée un handle de métafichier.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Ferme un contexte de périphérique de métafichier amélioré et crée un handle de métafichier amélioré.|
|[CMetaFileDC :: Create](#create)|Crée le contexte de périphérique de métafichier Windows et l’attache à l' `CMetaFileDC` objet.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Crée un contexte de périphérique de métafichier pour un métafichier de format amélioré.|

## <a name="remarks"></a>Notes

Pour implémenter un métafichier Windows, commencez par créer un `CMetaFileDC` objet. Appelez le `CMetaFileDC` constructeur, puis appelez la fonction membre [Create](#create) , qui crée un contexte de périphérique de métafichier Windows et l’attache à l' `CMetaFileDC` objet.

Envoyez ensuite l' `CMetaFileDC` objet à la séquence de commandes GDI CDC que vous avez l’intention de relire. Seules les commandes GDI qui créent une sortie, telles que `MoveTo` et `LineTo` , peuvent être utilisées.

Une fois que vous avez envoyé les commandes souhaitées au métafichier, appelez la `Close` fonction membre, qui ferme les contextes de périphérique de métafichier et retourne un handle de métafichier. Supprimez ensuite l' `CMetaFileDC` objet.

[CDC ::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) peut ensuite utiliser le handle de métafichier pour lire le métafichier à plusieurs reprises. Le métafichier peut également être manipulé par des fonctions Windows telles que [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew), qui copie un métafichier sur le disque.

Lorsque le métafichier n’est plus nécessaire, supprimez-le de la mémoire avec la fonction Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) .

Vous pouvez également implémenter l' `CMetaFileDC` objet afin qu’il puisse gérer les appels de sortie et les appels GDI d’attribut tels que `GetTextExtent` . Un tel métafichier est plus flexible et peut plus facilement réutiliser le code GDI général, qui se compose souvent d’une combinaison d’appels de sortie et d’attribut. La `CMetaFileDC` classe hérite de deux contextes `m_hDC` de périphérique et `m_hAttribDC` , de CDC. Le `m_hDC` contexte de périphérique gère tous les appels de sortie de capture de données [modifiées](../../mfc/reference/cdc-class.md) GDI et le `m_hAttribDC` contexte de périphérique gère tous les appels d’attribut GDI GDI. Normalement, ces deux contextes de périphérique font référence au même appareil. Dans le cas de `CMetaFileDC` , l’attribut DC est défini sur NULL par défaut.

Créez un deuxième contexte de périphérique qui pointe vers l’écran, une imprimante ou un appareil autre qu’un métafichier, puis appelez la `SetAttribDC` fonction membre pour associer le nouveau contexte de périphérique à `m_hAttribDC` . Les appels GDI pour les informations seront désormais dirigés vers le nouveau `m_hAttribDC` . Les appels GDI de sortie sont dirigés vers `m_hDC` , qui représente le métafichier.

Pour plus d’informations sur `CMetaFileDC` , consultez [contextes de périphérique](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Spécifications

**En-tête :** afxext. h

## <a name="cmetafiledcclose"></a><a name="close"></a> CMetaFileDC :: Close

Ferme le contexte de périphérique de métafichier et crée un handle de métafichier Windows qui peut être utilisé pour lire le métafichier à l’aide de la fonction membre [CDC ::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) .

```
HMETAFILE Close();
```

### <a name="return-value"></a>Valeur renvoyée

HMETAFILE valide si la fonction réussit ; Sinon, NULL.

### <a name="remarks"></a>Notes

Le descripteur de métafichier Windows peut également être utilisé pour manipuler le métafichier avec des fonctions Windows telles que [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew).

Supprimez le métafichier après l’avoir utilisé en appelant la fonction [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) de Windows.

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a> CMetaFileDC::CloseEnhanced

Ferme un contexte de périphérique de métafichier amélioré et retourne un handle qui identifie un métafichier de format amélioré.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Valeur renvoyée

Handle d’un métafichier amélioré, en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Une application peut utiliser le descripteur de métafichier amélioré retourné par cette fonction pour effectuer les tâches suivantes :

- Afficher une image stockée dans un métafichier amélioré

- Créer des copies du métafichier amélioré

- Énumérer, modifier ou copier des enregistrements individuels dans le métafichier amélioré

- Récupérer une description facultative du contenu du métafichier à partir de l’en-tête de métafichier amélioré

- Récupérer une copie de l’en-tête de métafichier amélioré

- Récupérer une copie binaire du métafichier amélioré

- Énumérer les couleurs dans la palette facultative

- Convertir un métafichier de format amélioré en métafichier Windows

Lorsque l’application n’a plus besoin du descripteur de métafichier amélioré, elle doit libérer le handle en appelant la `DeleteEnhMetaFile` fonction Win32.

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a> CMetaFileDC::CMetaFileDC

Construisez un `CMetaFileDC` objet en deux étapes.

```
CMetaFileDC();
```

### <a name="remarks"></a>Notes

Tout d’abord, appelez `CMetaFileDC` , puis appelez `Create` , qui crée le contexte de périphérique de métafichier Windows et l’attache à l' `CMetaFileDC` objet.

## <a name="cmetafiledccreate"></a><a name="create"></a> CMetaFileDC :: Create

Construisez un `CMetaFileDC` objet en deux étapes.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszFilename*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null. Spécifie le nom de fichier du métafichier à créer. Si *lpszFilename* a la valeur null, un nouveau métafichier en mémoire est créé.

### <a name="return-value"></a>Valeur renvoyée

Une valeur différente de zéro si la fonction réussit ; sinon, 0.

### <a name="remarks"></a>Notes

Tout d’abord, appelez le constructeur `CMetaFileDC` , puis appelez `Create` , qui crée le contexte de périphérique de métafichier Windows et l’attache à l' `CMetaFileDC` objet.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a> CMetaFileDC::CreateEnhanced

Crée un contexte de périphérique pour un métafichier de format amélioré.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Paramètres

*pDCRef*<br/>
Identifie un appareil de référence pour le métafichier amélioré.

*lpszFileName*<br/>
Pointe vers une chaîne de caractères se terminant par un caractère null. Spécifie le nom de fichier du métafichier amélioré à créer. Si ce paramètre a la valeur NULL, le métafichier amélioré est basé sur la mémoire et son contenu est perdu lorsque l’objet est détruit ou lorsque la `DeleteEnhMetaFile` fonction Win32 est appelée.

*lpBounds*<br/>
Pointe vers une structure de données [Rect](/windows/win32/api/windef/ns-windef-rect) ou un objet [CRect](../../atl-mfc-shared/reference/crect-class.md) qui spécifie les dimensions en unités HIMETRIC (par incréments de 0,01 millimètre) de l’image à stocker dans le métafichier amélioré.

*lpszDescription*<br/>
Pointe vers une chaîne se terminant par zéro qui spécifie le nom de l’application qui a créé l’image, ainsi que le titre de l’image.

### <a name="return-value"></a>Valeur renvoyée

Handle du contexte de périphérique pour le métafichier amélioré, en cas de réussite ; Sinon, NULL.

### <a name="remarks"></a>Notes

Ce contrôleur de stockage peut être utilisé pour stocker une image indépendante du périphérique.

Windows utilise l’appareil de référence identifié par le paramètre *pDCRef* pour enregistrer la résolution et les unités de l’appareil sur lequel une image a été initialement affichée. Si le paramètre *pDCRef* a la valeur null, il utilise le périphérique d’affichage actuel pour référence.

Les membres gauche et supérieur de la `RECT` structure de données vers laquelle pointe le paramètre *lpBounds* doivent être plus petits que les membres Right et Bottom, respectivement. Les points situés le long des bords du rectangle sont inclus dans l’image. Si *lpBounds* a la valeur null, l’interface GDI (Graphics Device Interface) calcule les dimensions du plus petit rectangle qui peut encadrer l’image dessinée par l’application. Le paramètre *lpBounds* doit être fourni dans la mesure du possible.

La chaîne vers laquelle pointe le paramètre *lpszDescription* doit contenir un caractère null entre le nom de l’application et le nom de l’image, et doit se terminer par deux caractères null, par exemple « XYZ Graphics Editor\0Bald Eagle\0\0 », où \ 0 représente le caractère null. Si *lpszDescription* a la valeur null, il n’y a pas d’entrée correspondante dans l’en-tête de métafichier amélioré.

Les applications utilisent le DC créé par cette fonction pour stocker une image graphique dans un métafichier amélioré. Le handle identifiant ce contrôleur de périphérique peut être passé à toute fonction GDI.

Une fois qu’une application a stocké une image dans un métafichier amélioré, elle peut afficher l’image sur n’importe quel périphérique de sortie en appelant la `CDC::PlayMetaFile` fonction. Lorsque vous affichez l’image, Windows utilise le rectangle vers lequel pointe le paramètre *lpBounds* et les données de résolution de l’appareil de référence pour positionner et mettre à l’échelle l’image. Le contexte de périphérique retourné par cette fonction contient les mêmes attributs par défaut que ceux associés à un nouveau contrôleur de périphérique.

Les applications doivent utiliser la `GetWinMetaFileBits` fonction Win32 pour convertir un métafichier amélioré au format de métafichier Windows plus ancien.

Le nom de fichier du métafichier amélioré doit utiliser. Extension EMF.

## <a name="see-also"></a>Voir aussi

[Classe CDC](../../mfc/reference/cdc-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
