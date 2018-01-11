---
title: Classe de CWaitCursor | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs: C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1cf5c850158e445e7695b85e540b1e0c162e621c
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2018
---
# <a name="cwaitcursor-class"></a>Classe de CWaitCursor
Permet en une ligne d'afficher un curseur d'attente, généralement sous forme de sablier, pendant que vous effectuez une longue opération.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|Construit un `CWaitCursor` de l’objet et affiche le curseur d’attente.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|Restaure le curseur d’attente après sa modification.|  
  
## <a name="remarks"></a>Notes  
 `CWaitCursor`ne dispose pas d’une classe de base.  
  
 Windows bonnes pratiques de programmation nécessitent que vous Affrichez un curseur d’attente chaque fois que vous effectuez une opération qui prend un certain temps.  
  
 Pour afficher un curseur d’attente, uniquement de définir un `CWaitCursor` variable avant le code qui effectue l’opération de longue durée. Constructeur de l’objet entraîne automatiquement le curseur d’attente à afficher.  
  
 Lorsque l’objet est hors de portée (à la fin du bloc dans lequel la `CWaitCursor` objet est déclaré), son destructeur définit le curseur jusqu’au curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.  
  
> [!NOTE]
>  En raison de leurs constructeurs et les destructeurs fonctionnement, `CWaitCursor` toujours, les objets sont déclarés comme variables locales, elles ne sont jamais déclarées comme des variables globales ni alloués avec **nouveau**.  
  
 Si vous effectuez une opération qui peut entraîner le curseur à modifier, comme l’affichage d’une boîte de message ou la boîte de dialogue, l’appel de la [restaurer](#restore) fonction membre pour restaurer le curseur d’attente. Il s’agit d’appeler OK **restaurer** même lorsqu’un curseur d’attente est affiché.  
  
 Un autre pour afficher un curseur d’attente consiste à utiliser la combinaison de [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)et, éventuellement, [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). Toutefois, `CWaitCursor` est plus facile à utiliser, car vous n’avez pas besoin de définir le curseur jusqu’au curseur précédent lorsque vous avez terminé avec l’opération de longue durée.  
  
> [!NOTE]
>  MFC définit et restaure le curseur à l’aide de la [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor) fonction virtuelle. Vous pouvez remplacer cette fonction pour fournir un comportement personnalisé.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CWaitCursor`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwin.h  
  
## <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 Pour afficher un curseur d’attente, déclarez un `CWaitCursor` objet avant le code qui effectue l’opération de longue durée.  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>Notes  
 Le constructeur entraîne automatiquement le curseur d’attente à afficher.  
  
 Lorsque l’objet est hors de portée (à la fin du bloc dans lequel la `CWaitCursor` objet est déclaré), son destructeur définit le curseur jusqu’au curseur précédent. En d’autres termes, l’objet effectue automatiquement le nettoyage nécessaire.  
  
 Vous pouvez tirer parti du fait que le destructeur est appelé à la fin du bloc (qui peut être avant la fin de la fonction) pour que le curseur d’attente active dans uniquement une partie de votre fonction. Cette technique est illustrée dans le deuxième exemple ci-dessous.  
  
> [!NOTE]
>  En raison de leurs constructeurs et les destructeurs fonctionnement, `CWaitCursor` toujours, les objets sont déclarés comme variables locales, elles ne sont jamais déclarées comme des variables globales, ni alloués avec **nouveau**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 Pour restaurer le curseur d’attente, appelez cette fonction après une opération, comme l’affichage d’une boîte de message ou de la boîte de dialogue peut changer le curseur d’attente à un autre curseur.  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>Notes  
 Il s’agit d’appeler OK **restaurer** même lorsque le curseur d’attente est affiché.  
  
 Si vous devez restaurer le curseur d’attente dans une fonction différente de celle dans laquelle le `CWaitCursor` objet est déclaré, vous pouvez appeler [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [Comment faire : modifier le curseur de souris dans une Application Microsoft Foundation](http://go.microsoft.com/fwlink/p/?linkid=128044)



