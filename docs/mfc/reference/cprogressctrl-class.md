---
title: CProgressCtrl (classe) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 38ccc4acfdfd618bf0fa11f4a49c1e0b78f009ca
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079388"
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (classe)
Fournit les fonctionnalités du contrôle commun de barre de progression Windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construit un objet `CProgressCtrl`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CProgressCtrl::Create](#create)|Crée un contrôle de barre de progression et l’attache à un `CProgressCtrl` objet.|  
|[CProgressCtrl::CreateEx](#createex)|Crée un contrôle de progression avec les styles étendus Windows spécifiés et l’attache à un `CProgressCtrl` objet.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtient la couleur de la barre de progression pour le contrôle de barre de progression actuel.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtient la couleur d’arrière-plan de la barre de progression actuel.|  
|[CProgressCtrl::GetPos](#getpos)|Obtient la position actuelle de la barre de progression.|  
|[CProgressCtrl::GetRange](#getrange)|Obtient les limites inférieures et supérieures de la plage du contrôle de barre de progression.|  
|[CProgressCtrl::GetState](#getstate)|Obtient l’état du contrôle de barre de progression actuel.|  
|[CProgressCtrl::GetStep](#getstep)|Récupère l’incrément de l’étape de la barre de progression du contrôle de barre de progression actuel.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Avance la position actuelle d’un contrôle de barre de progression d’un incrément spécifié et redessine la barre pour refléter la nouvelle position.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Définit la couleur de la barre de progression dans le contrôle de barre de progression actuel.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Définit la couleur d’arrière-plan de la barre de progression.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Désactive le mode de sélection ou désactiver pour le contrôle de barre de progression actuel.|  
|[CProgressCtrl::SetPos](#setpos)|Définit la position actuelle d’un contrôle de barre de progression et redessine la barre pour refléter la nouvelle position.|  
|[CProgressCtrl::SetRange](#setrange)|Définit les plages minimales et maximales pour un contrôle de barre de progression et redessine la barre pour refléter les nouvelles plages.|  
|[CProgressCtrl::SetState](#setstate)|Définit l'état du contrôle de barre de progression actuel.|  
|[CProgressCtrl::SetStep](#setstep)|Spécifie l’incrément de l’étape d’un contrôle de barre de progression.|  
|[CProgressCtrl::StepIt](#stepit)|Avance la position actuelle d’un contrôle de barre de progression de l’incrément de l’étape (consultez [SetStep](#setstep)) et redessine la barre pour refléter la nouvelle position.|  
  
## <a name="remarks"></a>Notes  
 Un contrôle de barre de progression est une fenêtre qu’une application peut utiliser pour indiquer la progression d’une opération longue. Il se compose d’un rectangle qui se remplit progressivement, de gauche à droite, avec le système de couleur de surbrillance qu’une opération progresse.  
  
 Un contrôle de barre de progression a une plage et une position actuelle. La plage représente la durée totale de l’opération, et la position actuelle représente la progression de que l’application a effectué l’opération. La procédure de fenêtre utilise la plage et la position actuelle pour déterminer le pourcentage de la barre de progression à remplir avec la couleur de surbrillance. Étant donné que la plage et les valeurs actuelles de position sont exprimés en tant qu’entiers signés, la plage de valeurs de position actuelle possibles provient allant de -2,147,483,648 à 2 147 483 647 inclus.  
  
 Pour plus d’informations sur l’utilisation de `CProgressCtrl`, consultez [contrôles](../../mfc/controls-mfc.md) et [à l’aide de CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmn.h  
  
##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl  
 Construit un objet `CProgressCtrl`.  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>Notes  
 Après avoir construit la `CProgressCtrl` de l’objet, appelez `CProgressCtrl::Create` pour créer le contrôle de barre de progression.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Crée un contrôle de barre de progression et l’attache à un `CProgressCtrl` objet.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwStyle*  
 Spécifie le style du contrôle de barre de progression. Appliquer n’importe quelle combinaison de stylesdescribed fenêtre dans [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) dans le Kit de développement logiciel Windows, en plus de la barre des styles de contrôle, au contrôle de progression suivante :  
  
- `PBS_VERTICAL` Affiche des informations de progression verticalement, de haut en bas. Sans cet indicateur, le contrôle de barre de progression affiche horizontalement, de gauche à droite.  
  
- `PBS_SMOOTH` Affiche progressive, lisse remplissage dans le contrôle de barre de progression. Sans cet indicateur, le contrôle remplit avec des blocs.  
  
 *Rect*  
 Spécifie la taille et la position du contrôle de barre de progression. Il peut être soit un [CRect](../../atl-mfc-shared/reference/crect-class.md) objet ou un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure. Étant donné que le contrôle doit être une fenêtre enfant, les coordonnées spécifiées sont par rapport à la zone cliente de la *pParentWnd*.  
  
 *pParentWnd*  
 Spécifie l’état d’avancement de la fenêtre parente du contrôle barre généralement un `CDialog`. Il ne doit pas être **NULL.**  
  
 *nID*  
 Spécifie l’ID de. du contrôle de barre de progression  
  
### <a name="return-value"></a>Valeur de retour  
 **TRUE** si le `CProgressCtrl` objet est correctement créé ; sinon **FALSE**.  
  
### <a name="remarks"></a>Notes  
 Vous construisez un `CProgressCtrl` objet en deux étapes. Tout d’abord, appelez le constructeur, ce qui crée le `CProgressCtrl` de l’objet, puis appelez `Create`, ce qui crée le contrôle de barre de progression.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 Crée un contrôle (une fenêtre enfant) et l’associe le `CProgressCtrl` objet.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Paramètres  
 *dwExStyle*  
 Spécifie le style étendu du contrôle en cours de création. Pour obtenir la liste des styles étendus de Windows, consultez le *dwExStyle* paramètre [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) dans le Kit de développement logiciel Windows.  
  
 *dwStyle*  
 Spécifie le style du contrôle de barre de progression. Appliquer n’importe quelle combinaison de styles de fenêtre décrit dans [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) dans le Kit de développement logiciel Windows.  
  
 *Rect*  
 Une référence à un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) structure décrivant la taille et la position de la fenêtre doit être créée, en coordonnées clientes de *pParentWnd*.  
  
 *pParentWnd*  
 Pointeur vers la fenêtre qui est le parent du contrôle.  
  
 *nID*  
 ID de fenêtre enfant. du contrôle  
  
### <a name="return-value"></a>Valeur de retour  
 Valeur différente de zéro cas de réussite ; sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Utilisez `CreateEx` au lieu de [créer](#create) pour appliquer des styles étendus Windows spécifiés par la préface style étendu de Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Obtient la couleur de la barre de progression pour le contrôle de barre de progression actuel.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur de la barre de progression actuel, représenté sous la forme un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur, ou `CLR_DEFAULT` si la couleur de barre de progression de l’indicateur est la couleur par défaut.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Obtient la couleur d’arrière-plan de la barre de progression actuel.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur d’arrière-plan de la barre de progression actuel, représenté sous la forme un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Récupère la position actuelle de la barre de progression.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La position du contrôle de barre de progression.  
  
### <a name="remarks"></a>Notes  
 La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais au lieu de cela est entre la limite supérieure et inférieure plage indiquée dans [SetRange](#setrange).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Obtient la limites inférieure et supérieure en cours, ou la plage, du contrôle de barre de progression.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Paramètres  
 *nLower*  
 Une référence à un entier de réception de la limite inférieure du contrôle de barre de progression.  
  
 *nUpper*  
 Une référence à un entier de réception de la limite supérieure du contrôle de barre de progression.  
  
### <a name="remarks"></a>Notes  
 Cette fonction copie les valeurs des limites inférieures et supérieures pour les entiers référencés par *nLower* et *nUpper*, respectivement.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl::GetState  
 Obtient l’état du contrôle de barre de progression actuel.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’état du contrôle de barre de progression actuel, qui est une des valeurs suivantes :  
  
|Value|État|  
|-----------|-----------|  
|`PBST_NORMAL`|En cours|  
|`PBST_ERROR`|Error|  
|`PBST_PAUSED`|Suspendu|  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant récupère l’état du contrôle de barre de progression actuel.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Récupère l’incrément de l’étape de la barre de progression du contrôle de barre de progression actuel.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 L’incrément de l’étape de la barre de progression.  
  
### <a name="remarks"></a>Notes  
 L’incrément de l’étape est le montant par lequel un appel à [CProgressCtrl::StepIt](#stepit) augmente la position actuelle de la barre de progression.  
  
 Cette méthode envoie le [PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant récupère l’incrément de l’étape de contrôle de barre de progression actuel.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Avance l’incrément spécifié par la barre la position actuelle du contrôle de progression *nPos* et redessine la barre pour refléter la nouvelle position.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Quantité d’avancer la position.  
  
### <a name="return-value"></a>Valeur de retour  
 La position précédente du contrôle de barre de progression.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Définit la couleur de la barre de progression dans le contrôle de barre de progression actuel.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *clrBar*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur qui spécifie la nouvelle couleur de la barre de progression. Spécifiez `CLR_DEFAULT` pour provoquer la barre de progression utiliser la couleur par défaut.|  
  
### <a name="return-value"></a>Valeur de retour  
 La couleur précédente de la barre de progression, représenté sous la forme un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur, ou `CLR_DEFAULT` si la couleur de la barre de progression est la couleur par défaut.  
  
### <a name="remarks"></a>Notes  
 Le `SetBarColor` méthode définit la progression de la barre uniquement si de couleur un [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] [thème](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx) n’est pas en vigueur.  
  
 Cette méthode envoie le [PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant modifie la couleur de la barre de progression pour le rouge, vert, bleu ou la valeur par défaut.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Définit la couleur d’arrière-plan de la barre de progression.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Paramètres  
 *clrNew*  
 A **COLORREF** valeur qui spécifie la couleur d’arrière-plan. Spécifiez le `CLR_DEFAULT` valeur à utiliser la couleur d’arrière-plan par défaut pour la barre de progression.  
  
### <a name="return-value"></a>Valeur de retour  
 Le [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valeur indiquant la couleur d’arrière-plan précédente, ou **CLR_DEFAULT** si la couleur d’arrière-plan est la couleur par défaut.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Désactive le mode de sélection ou désactiver pour le contrôle de barre de progression actuel.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *fMarqueeMode*|`true` Pour activer le mode de sélection, ou `false` pour désactiver le mode de sélection.|  
|[in] *%n%nintervalle*|Durée en millisecondes entre les mises à jour de l’animation du texte défilant.|  
  
### <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne toujours la valeur `true`.  
  
### <a name="remarks"></a>Notes  
 Lorsque le mode de sélection est activé, la barre de progression est animée et fait défiler comme une connexion sur un texte défilant cinéma.  
  
 Cette méthode envoie le [PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Exemple  
 L’exemple de code suivant démarre et arrête l’animation défilant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Définit la progression de la barre position actuelle du contrôle tel que spécifié par *nPos* et redessine la barre pour refléter la nouvelle position.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Paramètres  
 *nPos*  
 Nouvelle position du contrôle de barre de progression.  
  
### <a name="return-value"></a>Valeur de retour  
 La position précédente du contrôle de barre de progression.  
  
### <a name="remarks"></a>Notes  
 La position du contrôle de barre de progression n’est pas l’emplacement physique sur l’écran, mais au lieu de cela est entre la limite supérieure et inférieure plage indiquée dans [SetRange](#setrange).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Définit les limites supérieures et inférieures de la barre de plage du contrôle de progression et redessine la barre pour refléter les nouvelles plages.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Paramètres  
 *nLower*  
 Spécifie la limite inférieure de la plage (valeur par défaut est égale à zéro).  
  
 *nUpper*  
 Spécifie la limite supérieure de la plage (valeur par défaut est 100).  
  
### <a name="remarks"></a>Notes  
 La fonction membre `SetRange32` définit la plage de 32 bits pour le contrôle de progression.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 Définit l'état du contrôle de barre de progression actuel.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] *iState*|État pour définir la barre de progression. Utilisez l'une des valeurs suivantes :<br /><br /> - `PBST_NORMAL` -En cours<br />- `PBST_ERROR` -Erreur<br />- `PBST_PAUSED` -En pause|  
  
### <a name="return-value"></a>Valeur de retour  
 État précédent du contrôle de barre de progression actuel.  
  
### <a name="remarks"></a>Notes  
 Cette méthode envoie le [PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850) message, ce qui est décrit dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant définit la variable, `m_progressCtrl`, qui permet d'accéder par programmation au contrôle de barre de progression. Cette variable est utilisée dans l'exemple suivant.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Exemple  
 L'exemple de code suivant attribue au contrôle de barre de progression actuel l'état En pause ou Suspendu.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 Spécifie l’incrément de l’étape d’un contrôle de barre de progression.  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>Paramètres  
 *nEtape*  
 Nouvel incrément de l’étape.  
  
### <a name="return-value"></a>Valeur de retour  
 L’incrément étape précédente.  
  
### <a name="remarks"></a>Notes  
 L’incrément de l’étape est le montant par lequel un appel à `CProgressCtrl::StepIt` augmente la progression de la barre de la position actuelle.  
  
 L’incrément d’étape par défaut est 10.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Avance la position actuelle d’un contrôle de barre de progression de l’incrément de l’étape et redessine la barre pour refléter la nouvelle position.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Valeur de retour  
 La position précédente du contrôle de barre de progression.  
  
### <a name="remarks"></a>Notes  
 L’incrément de l’étape est définie par le `CProgressCtrl::SetStep` fonction membre.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [MFC exemple CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd (classe)](../../mfc/reference/cwnd-class.md)   
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)


