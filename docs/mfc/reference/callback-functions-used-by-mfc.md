---
title: Fonctions de rappel utilisées par MFC
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 9e51774b2158a81fce05dc0bd27e296e4ad94faa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507696"
---
# <a name="callback-functions-used-by-mfc"></a>Fonctions de rappel utilisées par MFC

Trois fonctions de rappel s’affichent dans le bibliothèque MFC (Microsoft Foundation Class). Ces fonctions de rappel sont passées à [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)et [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc). Notez que toutes les fonctions de rappel doivent intercepter les exceptions MFC avant de retourner à Windows, car les exceptions ne peuvent pas être levées au-delà des limites de rappel. Pour plus d’informations sur les exceptions, consultez l’article [exceptions](../../mfc/exception-handling-in-mfc.md).

|Name||
|----------|-----------------|
|[Fonction de rappel pour CDC::EnumObjects](#enum_objects)||
|[Fonction de rappel pour CDC::GrayString](#graystring)||
|[Fonction de rappel pour CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

## <a name="enum_objects"></a>Fonction de rappel pour CDC:: EnumObjects

Le nom *ObjectFunc* est un espace réservé pour le nom de la fonction fournie par l’application.

### <a name="syntax"></a>Syntaxe

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Paramètres

*lpszLogObject*<br/>
Pointe vers une structure de données [logpen,](/windows/win32/api/Wingdi/ns-wingdi-logpen) ou [logbrush,](/windows/win32/api/wingdi/ns-wingdi-logbrush) qui contient des informations sur les attributs logiques de l’objet.

*lpData*<br/>
Pointe vers les données fournies par l’application passées à `EnumObjects` la fonction.

### <a name="return-value"></a>Valeur de retour

La fonction de rappel retourne un **entier**. La valeur de ce retour est définie par l’utilisateur. Si la fonction de rappel retourne 0 `EnumObjects` , arrête l’énumération tôt.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté.

## <a name="graystring"></a>Fonction de rappel pour CDC:: GrayString

*OutputFunc* est un espace réservé pour le nom de la fonction de rappel fournie par l’application.

### <a name="syntax"></a>Syntaxe

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Paramètres

*hDC*<br/>
Identifie un contexte de périphérique de mémoire avec une image bitmap d’au moins la largeur et `nWidth` la `nHeight` hauteur `GrayString`spécifiées par et à.

*lpData*<br/>
Pointe vers la chaîne de caractères à ajouter.

*nCount*<br/>
Spécifie le nombre de caractères à afficher en sortie.

### <a name="return-value"></a>Valeur de retour

La valeur de retour de la fonction de rappel doit être TRUE pour indiquer la réussite; dans le cas contraire, la valeur est FALSe.

### <a name="remarks"></a>Notes

La fonction de rappel (*OutputFunc*) doit dessiner une image par rapport aux coordonnées (0,0) au lieu de (*x*, *y*).

## <a name="setabortproc"></a>Fonction de rappel pour CDC:: SetAbortProc

Le nom *AbortFunc* est un espace réservé pour le nom de la fonction fournie par l’application.

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
Spécifie si une erreur s’est produite. La valeur est 0 si aucune erreur n’est survenue. C’est SP_OUTOFDISK si le gestionnaire d’impression ne dispose pas de suffisamment d’espace disque et que de l’espace disque devient disponible si l’application attend. Si le *code* est SP_OUTOFDISK, l’application n’a pas besoin d’abandonner le travail d’impression. Si ce n’est pas le cas, il doit transmettre au gestionnaire d’impression `PeekMessage` en `GetMessage` appelant la fonction ou Windows.

### <a name="return-value"></a>Valeur de retour

La valeur de retour de la fonction de gestionnaire d’abandon est différente de zéro si le travail d’impression doit continuer, et 0 s’il est annulé.

### <a name="remarks"></a>Notes

Le nom réel doit être exporté comme décrit dans la section Notes de [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc).

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
