---
title: Fonctions de rappel utilisées par MFC | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.functions
dev_langs:
- C++
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce96d90506176812ffb70b580c9d95a38c65fa19
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350883"
---
# <a name="callback-functions-used-by-mfc"></a>Fonctions de rappel utilisées par MFC
Trois fonctions de rappel s’affichent dans la bibliothèque Microsoft Foundation Class. Ces fonctions de rappel sont passées à [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring), et [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc). Notez que toutes les fonctions de rappel doivent intercepter les exceptions MFC avant de retourner à Windows, étant donné que les exceptions ne peut pas être levées au-delà des limites de rappel. Pour plus d’informations sur les exceptions, consultez l’article [Exceptions](../../mfc/exception-handling-in-mfc.md).  

|Name||  
|----------|-----------------|  
|[Fonction de rappel pour CDC::EnumObjects](#enum_objects)||  
|[Fonction de rappel pour CDC::GrayString](#graystring)||
|[Fonction de rappel pour CDC::SetAbortProc](#setabortproc)|| 

## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwin.h 

## <a name="enum_objects"></a> Fonction de rappel pour CDC::EnumObjects
Le *ObjectFunc* nom est un espace réservé pour le nom de la fonction fournie par l’application.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszLogObject*  
 Pointe vers un [LOGPEN](../../mfc/reference/logpen-structure.md) ou [LOGBRUSH](../../mfc/reference/logbrush-structure.md) structure de données qui contient des informations sur les attributs de logiques de l’objet.  
  
 `lpData`  
 Points de données fourni par l’application passé à la `EnumObjects` (fonction).  
  
### <a name="return-value"></a>Valeur de retour  
 La fonction de rappel retourne un `int`. La valeur de ce retour est définie par l’utilisateur. Si la fonction de rappel retourne 0, `EnumObjects` arrête d’énumération au début.  
  
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
 `hDC`  
 Identifie un contexte de périphérique de mémoire avec une image bitmap d’au moins la largeur et la hauteur spécifiée par `nWidth` et `nHeight` à `GrayString`.  
  
 `lpData`  
 Pointe vers la chaîne de caractères à ajouter.  
  
 `nCount`  
 Spécifie le nombre de caractères en sortie.  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur de retour de la fonction de rappel doit être **TRUE** pour indiquer la réussite ; sinon, il est **FALSE**.  
  
### <a name="remarks"></a>Notes  
 La fonction de rappel (*OutputFunc*) doit dessiner une image par rapport aux coordonnées (0,0) plutôt que (*x*, *y*).  

## <a name="setabortproc"></a>  Fonction de rappel pour CDC::SetAbortProc
Le nom *AbortFunc* est un espace réservé pour le nom de la fonction fournie par l’application.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
### <a name="parameters"></a>Paramètres  
 *hPr*  
 Identifie le contexte de périphérique.  
  
 `code`  
 Spécifie si une erreur s’est produite. Il est 0 si aucune erreur ne s’est produite. Il s’agit de **SP_OUTOFDISK** si le Gestionnaire d’impression n’est pas l’espace disque et davantage d’espace disque devient disponible si l’application attend. Si `code` est **SP_OUTOFDISK**, l’application ne dispose pas d’annuler le travail d’impression. Si elle n’est pas le cas, elle doit générer pour le Gestionnaire d’impression en appelant le **PeekMessage** ou **GetMessage** fonction Windows.  
  
### <a name="return-value"></a>Valeur de retour  
 La valeur de retour de la fonction de gestionnaire d’abandon est différent de zéro si le travail d’impression pour continuer et 0 si elle est annulée.  
  
### <a name="remarks"></a>Notes  
 Le nom réel doit être exporté comme décrit dans la section Notes de [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc).  
 
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](structures-styles-callbacks-and-message-maps.md) [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects) [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc) [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)

