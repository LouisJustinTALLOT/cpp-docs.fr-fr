---
title: Fonctions de rappel utilisées par MFC
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.functions
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: acb7b6c677d03ef1320e24373671a7577c2ccda8
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178432"
---
# <a name="callback-functions-used-by-mfc"></a>Fonctions de rappel utilisées par MFC

Trois fonctions de rappel apparaissent dans la bibliothèque Microsoft Foundation Class. Ces fonctions de rappel sont passées à [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), et [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Notez que toutes les fonctions de rappel doivent intercepter les exceptions MFC avant de revenir à Windows, étant donné que les exceptions ne peut pas être levées au-delà des limites de rappel. Pour plus d’informations sur les exceptions, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

|Name||
|----------|-----------------|
|[Fonction de rappel pour CDC::EnumObjects](#enum_objects)||
|[Fonction de rappel pour CDC::GrayString](#graystring)||
|[Fonction de rappel pour CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="enum_objects"></a> Fonction de rappel pour CDC::EnumObjects

Le *ObjectFunc* nom est un espace réservé pour le nom de fonction fournie par l’application.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Paramètres

*lpszLogObject*<br/>
Pointe vers un [LOGPEN](/windows/desktop/api/Wingdi/ns-wingdi-taglogpen) ou [LOGBRUSH](/windows/desktop/api/wingdi/ns-wingdi-taglogbrush) structure de données qui contient des informations sur les attributs de logiques de l’objet.

*lpData*<br/>
Pointe vers les données fournie par l’application passé à la `EnumObjects` (fonction).

### <a name="return-value"></a>Valeur de retour

La fonction de rappel renvoie un **int**. La valeur de ce retour est défini par l’utilisateur. Si la fonction de rappel retourne 0, `EnumObjects` arrête l’énumération au début.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté.

## <a name="graystring"></a>  Fonction de rappel pour CDC::GrayString

*OutputFunc* est un espace réservé pour le nom de fonction de rappel fournie par l’application.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Paramètres

*hDC*<br/>
Identifie un contexte de périphérique de mémoire avec une image bitmap d’au moins la largeur et la hauteur spécifiée par `nWidth` et `nHeight` à `GrayString`.

*lpData*<br/>
Pointe vers la chaîne de caractères à ajouter.

*nCount*<br/>
Spécifie le nombre de caractères en sortie.

### <a name="return-value"></a>Valeur de retour

Valeur de retour de la fonction de rappel doit être TRUE pour indiquer la réussite ; Sinon, elle est FALSE.

### <a name="remarks"></a>Notes

La fonction de rappel (*OutputFunc*) doit dessiner une image relatif aux coordonnées (0,0) au lieu de (*x*, *y*).

## <a name="setabortproc"></a>  Fonction de rappel pour CDC::SetAbortProc

Le nom *AbortFunc* est un espace réservé pour le nom de fonction fournie par l’application.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Paramètres

*hPr*<br/>
Identifie le contexte de périphérique.

*code*<br/>
Spécifie si une erreur s’est produite. Il est 0 si aucune erreur ne se n’est produite. Il est SP_OUTOFDISK si le Gestionnaire d’impression est actuellement manque d’espace disque et davantage d’espace disque devient disponible si l’application attend. Si *code* est SP_OUTOFDISK, l’application ne devra pas abandonner le travail d’impression. Dans le cas contraire, elle doit générer pour le Gestionnaire d’impression en appelant le `PeekMessage` ou `GetMessage` (fonction) Windows.

### <a name="return-value"></a>Valeur de retour

La valeur de retour de la fonction de gestionnaire d’abandon est différent de zéro si le travail d’impression doit continuer et 0 si elle est annulée.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté comme décrit dans la section Notes de [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

