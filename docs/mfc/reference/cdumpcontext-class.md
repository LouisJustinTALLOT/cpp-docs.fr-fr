---
title: CDumpContext, classe
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: 3a81e06586e6de14d57ce4c4de36dc30c73383f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212512"
---
# <a name="cdumpcontext-class"></a>CDumpContext, classe

Prend en charge la sortie de diagnostic en fonction du flux dans un format contrôlable de visu.

## <a name="syntax"></a>Syntaxe

```
class CDumpContext
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDumpContext :: CDumpContext](#cdumpcontext)|Construit un objet `CDumpContext`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDumpContext ::D umpAsHex](#dumpashex)|Vide l’élément indiqué au format hexadécimal.|
|[CDumpContext :: Flush](#flush)|Vide toutes les données dans la mémoire tampon de contexte de vidage.|
|[CDumpContext :: GetDepth](#getdepth)|Obtient un entier correspondant à la profondeur du dump.|
|[CDumpContext :: HexDump](#hexdump)|Vide les octets contenus dans un tableau au format hexadécimal.|
|[CDumpContext :: SetDepth](#setdepth)|Définit la profondeur du dump.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDumpContext ::, opérateur&lt;&lt;](#operator_lt_lt)|Insère des variables et des objets dans le contexte de vidage.|

## <a name="remarks"></a>Notes

`CDumpContext`n’a pas de classe de base.

Vous pouvez utiliser [afxDump](diagnostic-services.md#afxdump), un objet prédéclaré `CDumpContext` , pour la plupart de votre vidage. L' `afxDump` objet est uniquement disponible dans la version de débogage du bibliothèque MFC (Microsoft Foundation Class).

Plusieurs [services de diagnostic](../../mfc/reference/diagnostic-services.md) de la mémoire utilisent `afxDump` pour leur sortie.

Dans l’environnement Windows, la sortie de l' `afxDump` objet prédéfini, conceptuellement similaire au `cerr` flux, est routée vers le débogueur via la fonction Windows `OutputDebugString` .

La `CDumpContext` classe a un opérateur d’insertion ( **<<** ) surchargé pour les `CObject` pointeurs qui vident les données de l’objet. Si vous avez besoin d’un format de vidage personnalisé pour un objet dérivé, remplacez [CObject ::D UMP](../../mfc/reference/cobject-class.md#dump). La plupart des classes Microsoft Foundation implémentent une `Dump` fonction membre substituée.

Les classes qui ne sont pas dérivées de `CObject` , telles que `CString` , `CTime` et `CTimeSpan` , ont leurs propres `CDumpContext` opérateurs d’insertion surchargés, comme les structures souvent utilisées, telles que `CFileStatus` , `CPoint` et `CRect` .

Si vous utilisez la macro [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) ou [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) dans l’implémentation de votre classe, `CObject::Dump` affiche le nom de votre `CObject` classe dérivée de. Dans le cas contraire, il s’imprimera `CObject` .

La `CDumpContext` classe est disponible avec les versions Debug et Release de la bibliothèque, mais la `Dump` fonction membre est définie uniquement dans la version Debug. Utilisez **#ifdef**  /  `#endif` instructions _DEBUG pour mettre en fourchette votre code de diagnostic, y compris vos `Dump` fonctions membres personnalisées.

Avant de créer votre propre `CDumpContext` objet, vous devez créer un `CFile` objet qui sert de destination de vidage.

Pour plus d’informations sur `CDumpContext` , consultez [débogage des applications MFC](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDumpContext`

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext :: CDumpContext

Construit un objet de classe `CDumpContext` .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Paramètres

*pFile*<br/>
Pointeur vers l' `CFile` objet qui est la destination du dump.

### <a name="remarks"></a>Notes

L' `afxDump` objet est construit automatiquement.

N’écrivez pas dans le sous-jacent `CFile` pendant que le contexte de vidage est actif ; sinon, vous risquez d’interférer avec le dump. Dans l’environnement Windows, la sortie est routée vers le débogueur via la fonction Windows `OutputDebugString` .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext ::D umpAsHex

Vide le type spécifié sous forme de nombres hexadécimaux.

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

Appelez cette fonction membre pour vider l’élément du type spécifié sous la forme d’un nombre hexadécimal. Pour vider un tableau, appelez [CDumpContext :: HexDump](#hexdump).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext :: Flush

Force l’écriture des données restantes dans les mémoires tampons dans le fichier attaché au contexte de vidage.

```cpp
void Flush();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext :: GetDepth

Détermine si un vidage profond ou superficiel est en cours.

```
int GetDepth() const;
```

### <a name="return-value"></a>Valeur de retour

Profondeur du dump définie par `SetDepth` .

### <a name="example"></a>Exemple

  Consultez l’exemple pour [SetDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext :: HexDump

Fait un dump d’un tableau d’octets au format hexadécimal.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Paramètres

*lpszLine*<br/>
Chaîne à générer au début d’une nouvelle ligne.

*pby*<br/>
Pointeur vers une mémoire tampon contenant les octets à vider.

*nBytes*<br/>
Nombre d’octets à vider.

*nWidth*<br/>
Nombre maximal d’octets vidés par ligne (pas la largeur de la ligne de sortie).

### <a name="remarks"></a>Notes

Pour vider un type d’élément spécifique unique sous forme de nombre hexadécimal, appelez [CDumpContext ::D umpashex](#dumpashex).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext ::, opérateur&lt;&lt;

Renvoie les données spécifiées dans le contexte de vidage.

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

Une référence `CDumpContext`. À l’aide de la valeur de retour, vous pouvez écrire plusieurs insertions sur une seule ligne de code source.

### <a name="remarks"></a>Notes

L’opérateur d’insertion est surchargé pour les `CObject` pointeurs et pour la plupart des types primitifs. Un pointeur vers un caractère produit un vidage du contenu de la chaîne ; un pointeur vers **`void`** renvoie une image de vidage hexadécimale de l’adresse uniquement. Un LONGLONG produit un vidage d’un entier signé 64 bits ; Un ULONGLONG produit un vidage d’un entier non signé 64 bits.

Si vous utilisez la macro IMPLEMENT_DYNAMIC ou IMPLEMENT_SERIAL dans l’implémentation de votre classe, alors l’opérateur d’insertion, via `CObject::Dump` , imprime le nom de votre `CObject` classe dérivée de. Dans le cas contraire, il s’imprimera `CObject` . Si vous substituez la `Dump` fonction de la classe, vous pouvez fournir une sortie plus significative du contenu de l’objet au lieu d’un vidage hexadécimal.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext :: SetDepth

Définit la profondeur de l’image mémoire.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Paramètres

*nNewDepth*<br/>
Nouvelle valeur de profondeur.

### <a name="remarks"></a>Notes

Si vous effectuez un vidage sur un type primitif ou simple `CObject` qui ne contient pas de pointeurs vers d’autres objets, la valeur 0 est suffisante. Une valeur supérieure à 0 spécifie un vidage profond où tous les objets sont vidés de manière récursive. Par exemple, un vidage approfondi d’une collection permet de vider tous les éléments de la collection. Vous pouvez utiliser d’autres valeurs de profondeur spécifiques dans vos classes dérivées.

> [!NOTE]
> Les références circulaires ne sont pas détectées dans les vidages profonds et peuvent entraîner des boucles infinies.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[CObject (classe)](../../mfc/reference/cobject-class.md)
