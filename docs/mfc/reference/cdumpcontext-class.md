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
ms.openlocfilehash: e89bbc5f263dc9303140e43914619090109b8315
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753208"
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
|[CDumpContext::CDumpContext](#cdumpcontext)|Construit un objet `CDumpContext`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|Décharge l’élément indiqué dans le format hexadecimal.|
|[CDumpContext::Flush](#flush)|Rincer toutes les données dans le mémoire des décharges tampon.|
|[CDumpContext::GetDepth](#getdepth)|Obtient un intégrant correspondant à la profondeur de la décharge.|
|[CDumpContext::HexDump](#hexdump)|Octets de décharges contenus dans un tableau en format hexadecimal.|
|[CDumpContext::SetDepth](#setdepth)|Définit la profondeur de la décharge.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CDumpContext::opérateur&lt;&lt;](#operator_lt_lt)|Insère les variables et les objets dans le contexte du dépotoir.|

## <a name="remarks"></a>Notes

`CDumpContext`n’a pas de classe de base.

Vous pouvez utiliser [afxDump](diagnostic-services.md#afxdump), `CDumpContext` un objet prédéclaré, pour la plupart de votre dumping. L’objet `afxDump` n’est disponible que dans la version Debug de la Microsoft Foundation Class Library.

Plusieurs des [services](../../mfc/reference/diagnostic-services.md) de `afxDump` diagnostic de mémoire utilisent pour leur sortie.

Sous l’environnement Windows, la sortie `afxDump` de l’objet prédéfini, conceptuellement similaire au `cerr` flux, `OutputDebugString`est acheminée vers le débbuggeur via la fonction Windows .

La `CDumpContext` classe dispose d’une **<<** insertion `CObject` surchargée ( ) opérateur pour les pointeurs qui décharge les données de l’objet. Si vous avez besoin d’un format de décharge personnalisé pour un objet dérivé, [remplacez CObject::Dump](../../mfc/reference/cobject-class.md#dump). La plupart des classes de `Dump` la Fondation Microsoft implémentent une fonction de membre surchargée.

Les classes qui `CObject`ne sont `CString` `CTime`pas `CTimeSpan`dérivées de , `CDumpContext` tels que , , et , `CFileStatus` `CPoint`ont `CRect`leurs propres opérateurs d’insertion surchargés, comme le font les structures souvent utilisées telles que , , et .

Si vous utilisez la [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) ou [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) macro dans la mise `CObject::Dump` en œuvre `CObject`de votre classe, alors imprimera le nom de votre classe dérivée. Sinon, il `CObject`imprimera .

La `CDumpContext` classe est disponible avec les versions Debug et `Dump` Release de la bibliothèque, mais la fonction membre n’est définie que dans la version Debug. Utilisez **#ifdef**  /  `#endif` _DEBUG des instructions pour saisir votre code diagnostique, y compris vos fonctions de membre personnalisé. `Dump`

Avant de créer `CDumpContext` votre propre objet, vous devez créer un `CFile` objet qui sert de destination de décharge.

Pour plus `CDumpContext`d’informations sur , voir [Debugging MFC Applications](/visualstudio/debugger/mfc-debugging-techniques).

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`CDumpContext`

## <a name="requirements"></a>Spécifications

**En-tête:** afx.h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpContext::CDumpContext

Construit un objet `CDumpContext`de classe .

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>Paramètres

*pFile (en)*<br/>
Un pointeur `CFile` à l’objet qui est la destination de décharge.

### <a name="remarks"></a>Notes

L’objet `afxDump` est construit automatiquement.

N’écrivez pas `CFile` au sous-jacent pendant que le contexte du dépotoir est actif; sinon, vous interférerez avec la décharge. Sous l’environnement Windows, la sortie est acheminée vers `OutputDebugString`le débbuggeur via la fonction Windows .

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpContext::DumpAsHex

Décharge le type spécifié formaté sous forme de nombres hexadecimal.

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

Appelez cette fonction de membre pour vider l’article du type spécifié comme un numéro hexadecimal. Pour vider un tableau, appelez [CDumpContext::HexDump](#hexdump).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpContext::Flush

Force toute donnée restante dans les tampons à être écrite au fichier attaché au contexte de décharge.

```cpp
void Flush();
```

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpContext::GetDepth

Détermine si un dépotoir profond ou peu profond est en cours.

```
int GetDepth() const;
```

### <a name="return-value"></a>Valeur de retour

La profondeur de la `SetDepth`décharge telle qu’elle est définie par .

### <a name="example"></a>Exemple

  Voir l’exemple pour [SetDepth](#setdepth).

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpContext::HexDump

Décharge une gamme d’octets formatés en nombres hexadecimal.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>Paramètres

*lpszLine (lpszLine)*<br/>
Une chaîne à la sortie au début d’une nouvelle ligne.

*Hydravion*<br/>
Un pointeur à un tampon contenant les octets à décharger.

*nBytes (en)*<br/>
Le nombre d’octets à vider.

*nWidth (en)*<br/>
Nombre maximum d’octets déversés par ligne (pas la largeur de la ligne de sortie).

### <a name="remarks"></a>Notes

Pour vider un seul type d’article spécifique comme un numéro hexadecimal, appelez [CDumpContext::DumpAsHex](#dumpashex).

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpContext::opérateur&lt;&lt;

Extrade les données spécifiées dans le contexte du dépotoir.

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

Une référence `CDumpContext`. En utilisant la valeur de retour, vous pouvez écrire plusieurs insertions sur une seule ligne de code source.

### <a name="remarks"></a>Notes

L’opérateur d’insertion `CObject` est surchargé pour les pointeurs ainsi que pour la plupart des types primitifs. Un pointeur au caractère entraîne un dépotoir de contenu de chaîne; un pointeur pour **annuler** les résultats dans un dépotoir hexadecimal de l’adresse seulement. Un LONGLONG donne lieu à un dépotoir d’un intégrant signé 64 bits; Un ULONGLONG se traduit par un dépotoir d’un integer non signé 64 bits.

Si vous utilisez le IMPLEMENT_DYNAMIC ou IMPLEMENT_SERIAL macro dans la mise en œuvre de votre classe, alors l’opérateur d’insertion, par le biais, `CObject::Dump`imprimera le nom de votre `CObject`classe dérivée. Sinon, il `CObject`imprimera . Si vous remplacez la `Dump` fonction de la classe, alors vous pouvez fournir une sortie plus significative du contenu de l’objet au lieu d’un dépotoir hexadecimal.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpContext::SetDepth

Définit la profondeur pour le dépotoir.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>Paramètres

*nNewDepth*<br/>
La nouvelle valeur de profondeur.

### <a name="remarks"></a>Notes

Si vous jettent un `CObject` type primitif ou simple qui ne contient pas de pointeurs à d’autres objets, alors une valeur de 0 est suffisante. Une valeur supérieure à 0 spécifie un dépotoir profond où tous les objets sont déversés de façon récursive. Par exemple, un dépotoir profond d’une collection videra tous les éléments de la collection. Vous pouvez utiliser d’autres valeurs de profondeur spécifiques dans vos classes dérivées.

> [!NOTE]
> Les références circulaires ne sont pas détectées dans des décharges profondes et peuvent entraîner des boucles infinies.

### <a name="example"></a>Exemple

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CFile, classe](../../mfc/reference/cfile-class.md)<br/>
[Classe CObject](../../mfc/reference/cobject-class.md)
