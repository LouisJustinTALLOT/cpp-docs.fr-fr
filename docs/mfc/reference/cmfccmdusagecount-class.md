---
title: Classe de CMFCCmdUsageCount | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
dev_langs: C++
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0db24894777170d2860ba8d1639fd44e3893732a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cmfccmdusagecount-class"></a>Classe de CMFCCmdUsageCount
Effectue le suivi du nombre d’utilisations des messages Windows, tels que lorsque l’utilisateur sélectionne un élément dans un menu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCCmdUsageCount : public CObject  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|||  
|-|-|  
|Nom|Description|  
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|Constructeur par défaut.|  
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|Destructeur.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|Nom|Description|  
|[CMFCCmdUsageCount::AddCmd](#addcmd)|Incrémente d’une unité le compteur est associé à la commande donnée.|  
|[CMFCCmdUsageCount::GetCount](#getcount)|Récupère le nombre total d’utilisation qui est associé à l’ID de commande donné.|  
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|Détermine si cet objet a collectées à la quantité minimale de données de suivi.|  
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|Détermine si la commande donnée est fréquemment utilisée.|  
|[CMFCCmdUsageCount::Reset](#reset)|Efface le décompte d’utilisation de toutes les commandes.|  
|[CMFCCmdUsageCount::Serialize](#serialize)|Lit de cet objet à partir d’une archive ou écrit dans une archive. (Substitue [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize).)|  
|[CMFCCmdUsageCount::SetOptions](#setoptions)|Définit les valeurs de partagées `CMFCCmdUsageCount` données membres de classe.|  
  
### <a name="data-members"></a>Membres de données  
  
|||  
|-|-|  
|Name|Description|  
|`m_CmdUsage`|Un `CMap` qui mappe des commandes pour le nombre de leur utilisation.|  
|`m_nMinUsagePercentage`|Le pourcentage minimal d’utilisation pour une commande à être fréquemment utilisés.|  
|`m_nStartCount`|Le compteur de démarrage qui est utilisé pour déterminer si cet objet a collecté la quantité minimale de données de suivi.|  
|`m_nTotalUsage`|Le nombre de commandes de tous les suivis.|  
  
### <a name="remarks"></a>Notes  
 La `CMFCCmdUsageCount` classe mappe chaque identificateur de message Windows numérique à un compteur de l’entier non signé 32 bits. `CMFCToolBar`utilise cette classe pour afficher les éléments fréquemment utilisés. Pour plus d’informations sur `CMFCToolBar`, consultez [CMFCToolBar classe](../../mfc/reference/cmfctoolbar-class.md).  
  
 Vous pouvez rendre persistante `CMFCCmdUsageCount` classe les données entre les exécutions de votre programme. Utilisez le [CMFCCmdUsageCount::Serialize](#serialize) méthode pour sérialiser les données de membre de classe et le [CMFCCmdUsageCount::SetOptions](#setoptions) pour définir les données de membre partagé.  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxcmdusagecount.h  
  
##  <a name="addcmd"></a>CMFCCmdUsageCount::AddCmd  
 Incrémente d’une unité le compteur est associé à la commande donnée.  
  
```  
void AddCmd(UINT uiCmd);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `uiCmd`|Spécifie le compteur de commande à incrémenter.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode ajoute une nouvelle entrée à la structure de mappage des nombres de la commande, de `m_CmdUsage`, si l’entrée n’existe pas déjà.  
  
 Cette méthode ne fait rien dans les cas suivants :  
  
-   L’infrastructure de la barre d’outils est en mode de personnalisation (le [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode) méthode retourne une valeur différente de zéro).  
  
-   La commande fait référence à un séparateur de menu ou sous-menu ( `uiCmd` est égal à 0 ou -1).  
  
- `uiCmd`fait référence à une commande standard (global `IsStandardCommand` fonction retourne une valeur différente de zéro).  
  
##  <a name="getcount"></a>CMFCCmdUsageCount::GetCount  
 Récupère le nombre total d’utilisation qui est associé à l’ID de commande donné.  
  
```  
UINT GetCount(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `uiCmd`|ID du compteur de commande à récupérer.|  
  
### <a name="return-value"></a>Valeur de retour  
 Le décompte d’utilisation qui est associé à l’ID de commande donné.  
  
##  <a name="hasenoughinformation"></a>CMFCCmdUsageCount::HasEnoughInformation  
 Détermine si cet objet a reçu la quantité minimale de données de suivi.  
  
```  
BOOL HasEnoughInformation() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si cet objet a reçu la quantité minimale de suivi des données ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne une valeur différente de zéro si le nombre total, `m_nTotalUsage`, suivies de toutes les commandes est égale ou supérieure au nombre initial, `m_nStartCount`. Par défaut, le framework définit le nombre initial de 0. Vous pouvez remplacer cette valeur en utilisant le [CMFCCmdUsageCount::SetOptions](#setoptions) (méthode).  
  
 Cette méthode est utilisée par [CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands) pour déterminer s’il faut afficher toutes les commandes de menu disponibles.  
  
##  <a name="isfreqeuntlyusedcmd"></a>CMFCCmdUsageCount::IsFreqeuntlyUsedCmd  
 Détermine si la commande donnée est fréquemment utilisée.  
  
```  
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;  
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `uiCmd`|Spécifie la commande à vérifier.|  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si la commande est fréquemment utilisée ; Sinon, 0.  
  
### <a name="remarks"></a>Notes  
 Cette méthode retourne 0 si l’utilisation de la commande total, `m_nTotalUsage`, est égal à 0. Sinon, cette méthode retourne zéro si le pourcentage de laquelle la commande spécifiée est utilisée est supérieur au pourcentage minimal, `m_nMinUsagePercentage`. Par défaut, le framework définit le pourcentage minimal à 5. Vous pouvez remplacer cette valeur en utilisant le [CMFCCmdUsageCount::SetOptions](#setoptions) (méthode). Si le pourcentage minimal est 0, cette méthode retourne zéro si le nombre de commandes spécifiée est supérieur à 0.  
  
 [CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused) utilise cette méthode pour déterminer si une commande est rarement utilisée.  
  
##  <a name="reset"></a>CMFCCmdUsageCount::Reset  
 Efface le décompte d’utilisation de toutes les commandes.  
  
```  
void Reset();
```  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour effacer toutes les entrées de la structure de mappage des nombres de la commande, `m_CmdUsage`et de réinitialiser l’utilisation de la commande total, `m_nTotalUsage`, compteur à 0.  
  
##  <a name="serialize"></a>CMFCCmdUsageCount::Serialize  
 Lit de cet objet à partir d’une archive ou écrit dans une archive.  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `ar`|A `CArchive` objet à sérialiser depuis ou vers.|  
  
### <a name="remarks"></a>Notes  
 Cette méthode sérialise des nombres de la commande, de la structure du plan `m_CmdUsage`et l’utilisation de la commande total, `m_nTotalUsage`, compteur ou de l’archive spécifiée.  
  
 Pour des exemples de sérialisation, consultez [sérialisation : sérialisation d’un objet](../../mfc/serialization-serializing-an-object.md).  
  
##  <a name="setoptions"></a>CMFCCmdUsageCount::SetOptions  
 Définit les valeurs de partagées `CMFCCmdUsageCount` données membres de classe.  
  
```  
static BOOL __stdcall SetOptions(
    UINT nStartCount,  
    UINT nMinUsagePercentage);
```  
  
### <a name="parameters"></a>Paramètres  
  
|||  
|-|-|  
|Paramètre|Description|  
|[in] `nStartCount`|Le nouveau nombre initial de commandes de tous les suivis.|  
|[in] `nMinUsagePercentage`|Le nouveau pourcentage minimal d’utilisation.|  
  
### <a name="return-value"></a>Valeur de retour  
 `TRUE`Si la méthode réussit, `FALSE` si le `nMinUsagePercentage` paramètre est supérieure ou égale à 100.  
  
### <a name="remarks"></a>Notes  
 Cette méthode définit le partagé `CMFCCmdUsageCount` données membres de classe `m_nStartCount` et `m_nMinUsagePercentage` à `nStartCount` et `nMinUsagePercentage`, respectivement. `m_nStartCount`est utilisé par le [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation) méthode pour déterminer si cet objet a collecté la quantité minimale de données de suivi. `m_nMinUsagePercentage`est utilisé par le [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd) méthode pour déterminer si une commande donnée est fréquemment utilisée.  
  
 Dans les versions Debug cette méthode génère un échec d’assertion si le `nMinUsagePercentage` paramètre est supérieure ou égale à 100.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar, classe](../../mfc/reference/cmfctoolbar-class.md)
