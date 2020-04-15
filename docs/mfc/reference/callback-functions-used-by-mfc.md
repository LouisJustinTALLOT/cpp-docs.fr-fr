---
title: Fonctions de rappel utilisées par MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371136"
---
# <a name="callback-functions-used-by-mfc"></a>Fonctions de rappel utilisées par MFC

Trois fonctions de rappel apparaissent dans la bibliothèque de classe microsoft Foundation. Ces fonctions de rappel sont transmises à [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), et [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Notez que toutes les fonctions de rappel doivent piéger les exceptions MFC avant de revenir à Windows, puisque les exceptions ne peuvent pas être jetées au-delà des limites de rappel. Pour plus d’informations sur les exceptions, voir l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).

|Nom||
|----------|-----------------|
|[Fonction de rappel pour CDC::EnumObjects](#enum_objects)||
|[Fonction de rappel pour CDC::GrayString](#graystring)||
|[Fonction de rappel pour CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Fonction de rappel pour CDC::EnumObjects

Le nom *ObjectFunc* est un lieu réservé pour le nom de fonction fourni par l’application.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Paramètres

*lpszLogObject*<br/>
Indique une structure de données [LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen) ou [LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur les attributs logiques de l’objet.

*lpData (lpData)*<br/>
Indique les données fournies par `EnumObjects` l’application transmises à la fonction.

### <a name="return-value"></a>Valeur de retour

La fonction de rappel renvoie un **int**. La valeur de ce retour est définie par l’utilisateur. Si la fonction de rappel `EnumObjects` revient 0, arrête le recensement tôt.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Fonction de rappel pour CDC::GrayString

*OutputFunc* est un lieu réservé pour le nom de fonction de rappel fourni par l’application.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Paramètres

*Hdc*<br/>
Identifie un contexte de dispositif de mémoire avec une bitmap `nHeight` `GrayString`d’au moins la largeur et la hauteur spécifiées par `nWidth` et à .

*lpData (lpData)*<br/>
Pointe vers la chaîne de caractères à ajouter.

*nCompte*<br/>
Spécifie le nombre de caractères à la sortie.

### <a name="return-value"></a>Valeur de retour

La valeur de retour de la fonction de rappel doit être VRAI pour indiquer le succès; sinon c’est FALSE.

### <a name="remarks"></a>Notes

La fonction de rappel (*OutputFunc*) doit dessiner une image par rapport aux coordonnées (0,0) plutôt que *(x*, *y*).

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Fonction de rappel pour CDC::SetAbortProc

Le nom *AbortFunc* est un lieu réservé pour le nom de fonction fourni par l’application.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Paramètres

*Hpr*<br/>
Identifie le contexte de l’appareil.

*Code*<br/>
Précise si une erreur s’est produite. C’est 0 si aucune erreur n’a eu lieu. Il est SP_OUTOFDISK si le gestionnaire d’impression est actuellement hors de l’espace de disque et plus d’espace de disque deviendra disponible si l’application attend. Si *le code* est SP_OUTOFDISK, l’application n’a pas à interrompre le travail d’impression. Si ce n’est pas le cas, `PeekMessage` il `GetMessage` doit céder au gestionnaire d’impression en appelant la fonction ou Windows.

### <a name="return-value"></a>Valeur de retour

La valeur de retour de la fonction abort-handler est nonzero si le travail d’impression doit continuer, et 0 si elle est annulée.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté tel que décrit dans la section Remarques de [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
