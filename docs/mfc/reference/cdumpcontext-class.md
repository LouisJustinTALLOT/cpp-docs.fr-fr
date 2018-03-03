---
title: Classe de CDumpContext | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
dev_langs:
- C++
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5d54a461bece96faeb11f78a1788049abcabbae0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="cdumpcontext-class"></a>Classe de CDumpContext
Prend en charge la sortie de diagnostic en fonction du flux dans un format contrôlable de visu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CDumpContext  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDumpContext::CDumpContext](#cdumpcontext)|Construit un objet `CDumpContext`.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CDumpContext::DumpAsHex](#dumpashex)|Exporte l’élément indiqué au format hexadécimal.|  
|[CDumpContext::Flush](#flush)|Vide toutes les données dans le tampon de contexte de dump.|  
|[CDumpContext::GetDepth](#getdepth)|Obtient un entier correspondant à la profondeur de l’image mémoire.|  
|[CDumpContext::HexDump](#hexdump)|Vide les octets contenus dans un tableau au format hexadécimal.|  
|[CDumpContext::SetDepth](#setdepth)|Définit la profondeur de l’image mémoire.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|Insère des variables et des objets dans le contexte de dump.|  
  
## <a name="remarks"></a>Notes  
 `CDumpContext`ne dispose pas d’une classe de base.  
  
 Vous pouvez utiliser [afxDump](diagnostic-services.md#afxdump), un prédéclarée `CDumpContext` objet, pour la plupart de vos le vidage. Le `afxDump` objet est disponible uniquement dans la version Debug de la bibliothèque Microsoft Foundation Class.  
  
 Plusieurs de la mémoire [services de diagnostic](../../mfc/reference/diagnostic-services.md) utiliser `afxDump` pour leur sortie.  
  
 Dans l’environnement Windows, la sortie de prédéfinis `afxDump` objet, conceptuellement semblable à la `cerr` stream, est routé vers le débogueur via la fonction Windows **OutputDebugString**.  
  
 Le `CDumpContext` classe a une insertion surchargée (  **<<** ) opérateur pour `CObject` des pointeurs qui exporte les données de l’objet. Si vous avez besoin d’un format dump personnalisé pour un objet dérivé, substituez [CObject::Dump](../../mfc/reference/cobject-class.md#dump). La plupart des classes Microsoft Foundation implémentent substitué `Dump` fonction membre.  
  
 Les classes qui ne sont pas dérivés de `CObject`, tel que `CString`, `CTime`, et `CTimeSpan`, ont leurs propres surchargé `CDumpContext` des opérateurs d’insertion, en tant que structures souvent utilisé comme **CFileStatus**, `CPoint`, et `CRect`.  
  
 Si vous utilisez la [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) ou [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro dans l’implémentation de votre classe, puis `CObject::Dump` imprime le nom de votre `CObject`-classe dérivée. Dans le cas contraire, il imprime `CObject`.  
  
 Le `CDumpContext` classe n’est disponible avec les versions Debug et Release de la bibliothèque, mais la `Dump` fonction membre est définie uniquement dans la version Debug. Utilisez **#ifdef _DEBUG**  /  `#endif` instructions crochet de votre code de diagnostic, y compris vos `Dump` fonctions membres.  
  
 Avant de créer votre propre `CDumpContext` de l’objet, vous devez créer un `CFile` objet qui sert à la destination de vidage.  
  
 Pour plus d’informations sur `CDumpContext`, consultez [débogage des Applications MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
 **#define _DEBUG**  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 `CDumpContext`  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afx.h  
  
##  <a name="cdumpcontext"></a>CDumpContext::CDumpContext  
 Construit un objet de classe `CDumpContext`.  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>Paramètres  
 `pFile`  
 Un pointeur vers le `CFile` objet qui est la destination de vidage.  
  
### <a name="remarks"></a>Notes  
 Le `afxDump` objet est généré automatiquement.  
  
 Ne pas écrire de sous-jacent `CFile` alors que le contexte de dump est active ; sinon, vous interfère avec le vidage. Dans l’environnement Windows, la sortie est routée vers le débogueur via la fonction Windows **OutputDebugString**.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="dumpashex"></a>CDumpContext::DumpAsHex  
 Exporte le type spécifié sous formaté de nombres hexadécimaux.  
  
```  
CDumpContext& DumpAsHex(BYTE b);  
CDumpContext& DumpAsHex(DWORD dw);  
CDumpContext& DumpAsHex(int n);  
CDumpContext& DumpAsHex(LONG l);  
CDumpContext& DumpAsHex(LONGLONG n);  
CDumpContext& DumpAsHex(UINT u);  
CDumpContext& DumpAsHex(ULONGLONG n);  
CDumpContext& DumpAsHex(WORD w);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Référence à un objet `CDumpContext`.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction membre pour vider l’élément du type spécifié comme un nombre hexadécimal. Pour vider un tableau, appeler [CDumpContext::HexDump](#hexdump).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="flush"></a>CDumpContext::Flush  
 Force toutes les données restantes dans les mémoires tampon à écrire dans le fichier attaché dans le contexte de dump.  
  
```  
void Flush();
```  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="getdepth"></a>CDumpContext::GetDepth  
 Détermine si une image complète ou superficielle est en cours.  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 La profondeur de l’image en tant que jeu par `SetDepth`.  
  
### <a name="example"></a>Exemple  
  Consultez l’exemple de [SetDepth](#setdepth).  
  
##  <a name="hexdump"></a>CDumpContext::HexDump  
 Exporte un tableau d’octets sous formaté de nombres hexadécimaux.  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>Paramètres  
 *lpszLine*  
 Une chaîne de sortie au début d’une nouvelle ligne.  
  
 *pby*  
 Pointeur vers une mémoire tampon contenant les octets à vider.  
  
 `nBytes`  
 Le nombre d’octets à vider.  
  
 `nWidth`  
 Nombre maximal d’octets vidés par ligne (pas la largeur de la ligne de sortie).  
  
### <a name="remarks"></a>Notes  
 Pour vider un type d’élément spécifique unique, comme un nombre hexadécimal, appelez [CDumpContext::DumpAsHex](#dumpashex).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;  
 Génère les données spécifiées dans le contexte de dump.  
  
```  
CDumpContext& operator<<(const CObject* pOb);  
CDumpContext& operator<<(const CObject& ob);  
CDumpContext& operator<<(LPCTSTR lpsz);  
CDumpContext& operator<<(const void* lp);  
CDumpContext& operator<<(BYTE by);  
CDumpContext& operator<<(WORD w);  
CDumpContext& operator<<(DWORD dw);  
CDumpContext& operator<<(int n);  
CDumpContext& operator<<(double d);  
CDumpContext& operator<<(float f);  
CDumpContext& operator<<(LONG l);  
CDumpContext& operator<<(UINT u);  
CDumpContext& operator<<(LPCWSTR lpsz);  
CDumpContext& operator<<(LPCSTR lpsz);  
CDumpContext& operator<<(LONGLONG n);  
CDumpContext& operator<<(ULONGLONG n);  
CDumpContext& operator<<(HWND h);  
CDumpContext& operator<<(HDC h);  
CDumpContext& operator<<(HMENU h);  
CDumpContext& operator<<(HACCEL h);  
CDumpContext& operator<<(HFONT h);
```  
  
### <a name="return-value"></a>Valeur de retour  
 A `CDumpContext` référence. À l’aide de la valeur de retour, vous pouvez écrire plusieurs insertions sur une seule ligne de code source.  
  
### <a name="remarks"></a>Notes  
 L’opérateur d’insertion est surchargée pour `CObject` pointeurs ainsi que pour les types les plus primitifs. Un pointeur vers caractère se traduit par un dump du contenu de la chaîne ; un pointeur vers `void` entraîne un vidage hexadécimal de l’adresse. A **LONGLONG** des résultats dans un fichier de vidage d’un entier signé 64 bits ; A **ULONGLONG** des résultats dans un fichier de vidage d’un entier non signé 64 bits.  
  
 Si vous utilisez la `IMPLEMENT_DYNAMIC` ou `IMPLEMENT_SERIAL` macro dans l’implémentation de votre classe, puis l’opérateur d’insertion, via `CObject::Dump`, imprime le nom de votre `CObject`-classe dérivée. Dans le cas contraire, il imprime `CObject`. Si vous remplacez le `Dump` fonction de la classe, puis vous pouvez fournir une sortie plus significative de contenu de l’objet au lieu d’un fichier de vidage hexadécimal.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="setdepth"></a>CDumpContext::SetDepth  
 Définit la profondeur de l’image mémoire.  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>Paramètres  
 *nNewDepth*  
 La nouvelle valeur de profondeur.  
  
### <a name="remarks"></a>Notes  
 Si le dump d’un type primitif ou une simple `CObject` ne contenant aucun pointeur à d’autres objets, la valeur 0 est suffisante. Une valeur supérieure à 0 spécifie un fichier de vidage approfondie où tous les objets sont vidées de manière récursive. Par exemple, une image complète d’une collection vide tous les éléments de la collection. Vous pouvez utiliser les autres valeurs de profondeur spécifiques dans vos classes dérivées.  
  
> [!NOTE]
>  Les références circulaires ne sont pas détectés dans les dumps approfondies et peuvent entraîner une boucle infinie.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [CFile (classe)](../../mfc/reference/cfile-class.md)   
 [CObject, classe](../../mfc/reference/cobject-class.md)
