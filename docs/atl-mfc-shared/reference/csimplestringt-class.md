---
title: Classe de CSimpleStringT | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
dev_langs:
- C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a7dc68cd1d91cb7b651dbeb68422f6a89fb9f2f8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32366560"
---
# <a name="csimplestringt-class"></a>Classe de CSimpleStringT
Cette classe représente un `CSimpleStringT` objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>Paramètres  
 `BaseType`  
 Le type de caractère de la classe string. Il peut s'agir d'une des valeurs suivantes :  
  
- `char` (pour les chaînes de caractères ANSI).  
  
- `wchar_t` (pour les chaînes de caractères Unicode).  
  
- **TCHAR** (pour les chaînes de caractères ANSI et Unicode).  

## <a name="members"></a>Membres  
  
### <a name="public-typedefs"></a>Typedefs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|Pointeur vers une chaîne constante.|  
|[CSimpleStringT::PXSTR](#pxstr)|Un pointeur vers une chaîne.|  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|Construit `CSimpleStringT` objets de différentes manières.|  
|[CSimpleStringT :: ~ CSimpleStringT](#dtor)|Destructeur.|  

  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|Ajoute un `CSimpleStringT` à un objet `CSimpleStringT` objet.|  
|[CSimpleStringT::AppendChar](#appendchar)|Ajoute un caractère à un `CSimpleStringT` objet.|  
|[CSimpleStringT::CopyChars](#copychars)|Copie un ou plusieurs caractères dans une autre chaîne.|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Copie un ou plusieurs caractères dans une autre chaîne dans laquelle les mémoires tampons se chevauchent.|  
|[CSimpleStringT::Empty](#empty)|Force une chaîne a une longueur de zéro.|  
|[CSimpleStringT::FreeExtra](#freeextra)|Libère la mémoire supplémentaire précédemment alloué par l’objet string.|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|Récupère la longueur allouée d’un `CSimpleStringT` objet.|  
|[CSimpleStringT::GetAt](#getat)|Retourne le caractère à une position donnée.|  
|[CSimpleStringT::GetBuffer](#getbuffer)|Retourne un pointeur vers les caractères dans un `CSimpleStringT`.|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Retourne un pointeur vers les caractères dans un `CSimpleStringT`, la troncation de la longueur spécifiée.|  
|[CSimpleStringT::GetLength](#getlength)|Retourne le nombre de caractères dans un `CSimpleStringT` objet.|  
|[CSimpleStringT::GetManager](#getmanager)|Récupère le Gestionnaire de mémoire de le `CSimpleStringT` objet.|  
|[CSimpleStringT::GetString](#getstring)|Récupère la chaîne de caractères|  
|[CSimpleStringT::IsEmpty](#isempty)|Tests si un `CSimpleStringT` objet ne contient pas de caractères.|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|Désactive le décompte de références et protège la chaîne dans la mémoire tampon.|  
|[CSimpleStringT::Preallocate](#preallocate)|Alloue une quantité spécifique de mémoire pour la mémoire tampon de caractères.|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Contrôle de la mémoire tampon retournée par `GetBuffer`.|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Contrôle de la mémoire tampon retournée par `GetBuffer`.|  
|[CSimpleStringT::SetAt](#setat)|Définit un caractère à une position donnée.|  
|[CSimpleStringT::SetManager](#setmanager)|Définit le Gestionnaire de mémoire d’un `CSimpleStringT` objet.|  
|[CSimpleStringT::SetString](#setstring)|Définit la chaîne d’un `CSimpleStringT` objet.|  
|[CSimpleStringT::StringLength](#stringlength)|Retourne le nombre de caractères dans la chaîne spécifiée.|  
|[CSimpleStringT::Truncate](#truncate)|Tronque la chaîne d’une longueur spécifiée.|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Active le comptage des références et libère la chaîne dans la mémoire tampon.|  

### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Accède directement aux caractères stockés dans un `CSimpleStringT` objet comme une chaîne de style C.|  
|[CSimpleStringT::operator\[\]](#operator_at)|Retourne le caractère à une position donnée : substitution de l’opérateur pour `GetAt`.|  
|[CSimpleStringT::operator +=](#operator_add_eq)|Concatène une nouvelle chaîne à la fin d’une chaîne existante.|  
|[CSimpleStringT::operator =](#operator_eq)|Affecte une nouvelle valeur à un `CSimpleStringT` objet.|  
  
### <a name="remarks"></a>Notes  
 `CSimpleStringT` est la classe de base pour les différentes classes de chaîne prises en charge par Visual C++. Il fournit la prise en charge minimale pour la gestion de mémoire de l’objet de chaîne et la manipulation de base de mémoire tampon. Pour les objets de chaîne plus avancées, consultez [Classe CStringT](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="requirements"></a>Spécifications  
 **En-tête :** atlsimpstr.h  


## <a name="append"></a> CSimpleStringT::Append
Ajoute un `CSimpleStringT` à un objet `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Paramètres  
 `strSrc`  
 Le `CSimpleStringT` objet à ajouter.  
  
 `pszSrc`  
 Un pointeur vers une chaîne contenant les caractères à ajouter.  
  
 `nLength`  
 Nombre de caractères à ajouter.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour ajouter un existant `CSimpleStringT` objet vers un autre `CSimpleStringT` objet.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::Append`.  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="appendchar"></a> CSimpleStringT::AppendChar
Ajoute un caractère à un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>Paramètres  
 *ch*  
 Le caractère à ajouter  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour ajouter le caractère spécifié à la fin d’un objet `CSimpleStringT` objet.  
  
##  <a name="copychars"></a> CSimpleStringT::CopyChars  
 Copie un ou plusieurs caractères à une `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>Paramètres  
 `pchDest`  
 Pointeur vers une chaîne de caractères.  
  
 `pchSrc`  
 Un pointeur vers une chaîne contenant les caractères à copier.  
  
 `nChars`  
 Le nombre de `pchSrc` caractères à copier.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour copier les caractères à partir de `pchSrc` à la `pchDest` chaîne.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::CopyChars`.  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped
Copie un ou plusieurs caractères à une `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>Paramètres  
 `pchDest`  
 Pointeur vers une chaîne de caractères.  
  
 `pchSrc`  
 Un pointeur vers une chaîne contenant les caractères à copier.  
  
 `nChars`  
 Le nombre de `pchSrc` caractères à copier.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour copier les caractères à partir de `pchSrc` à la `pchDest` chaîne. Contrairement aux `CopyChars`, `CopyCharsOverlapped` fournit une méthode sûre pour la copie des mémoires tampon de caractères qui peut être fusionné.  
  
### <a name="example"></a>Exemple  
 Consultez l’exemple de [CSimpleStringT::CopyChars](#copychars), ou le code source pour `CSimpleStringT::SetString` (situé dans atlsimpstr.h).  
  
##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT  
 Construit un objet `CSimpleStringT`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>Paramètres  
 `strSrc`  
 Existant `CSimpleStringT` objet doit être copié dans ce `CSimpleStringT` objet.  
  
 `pchSrc`  
 Un pointeur vers un tableau de caractères de longueur `nLength`, pas terminer par null.  
  
 `pszSrc`  
 Une chaîne se terminant par null à copier dans cette `CSimpleStringT` objet.  
  
 `nLength`  
 Le nombre de caractères dans `pch`.  
  
 `pStringMgr`  
 Un pointeur vers le Gestionnaire de mémoire de le `CSimpleStringT` objet. Pour plus d’informations sur `IAtlStringMgr` et gestion de la mémoire pour `CSimpleStringT`, consultez [gestion de la mémoire et CStringT](../memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Notes  
 Construire une nouvelle `CSimpleStringT` objet. Étant donné que les constructeurs copient les données d’entrée dans le nouveau stockage alloué, les exceptions de mémoire peuvent entraîner.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de `CSimpleStringT::CSimpleStringT` à l’aide de la bibliothèque ATL `typedef` `CSimpleString`. `CSimpleString` est une spécialisation couramment utilisée de la classe de modèle `CSimpleStringT`.  
  
```cpp  
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"   
```

  
##  <a name="empty"></a>  CSimpleStringT::Empty
Convertit cette `CSimpleStringT` une chaîne vide de l’objet et libère la mémoire selon le cas.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>Notes  
 Pour plus d’informations, consultez [chaînes : nettoyage des exceptions CString](../cstring-exception-cleanup.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::Empty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra
Libère la mémoire supplémentaire précédemment alloué par la chaîne mais n’est plus nécessaire.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>Notes  
 Cela doit réduire la charge de mémoire consommée par l’objet string. La méthode réaffecte la mémoire tampon à la longueur exacte renvoyée par [GetLength](#getlength).  
  
### <a name="example"></a>Exemple  
```cpp  
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its 
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra 
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```
  
### <a name="remarks"></a>Notes  
 La sortie de cet exemple est la suivante :  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength  
Récupère la longueur allouée d’un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères alloués pour cet objet.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour déterminer le nombre de caractères alloué pour ce `CSimpleStringT` objet. Consultez [FreeExtra](#freeextra) pour obtenir un exemple d’appel de cette fonction.  
  
##  <a name="getat"></a>  CSimpleStringT::GetAt  
Retourne un caractère un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>Paramètres  
 `iChar`  
 Index de base zéro du caractère dans le `CSimpleStringT` objet. Le `iChar` paramètre doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength). Dans le cas contraire, `GetAt` génère une exception.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `XCHAR` qui contient le caractère situé à la position spécifiée dans la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour retourner le caractère spécifié par `iChar`. L’indice surchargé (`[]`) (opérateur) est un alias pratique pour `GetAt`. La marque de fin null est adressable sans générer d’exception à l’aide de `GetAt`. Toutefois, il n’est pas comptée par `GetLength`, et la valeur retournée est 0.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser `CSimpleStringT::GetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer  
Retourne un pointeur vers la mémoire tampon de caractères interne pour le `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>Paramètres  
 `nMinBufferLength`  
 Le nombre minimal de caractères que la mémoire tampon de caractères peut contenir. Cette valeur n’inclut pas d’espace pour un terminateur null.  
  
 Si `nMinBufferLength` est supérieure à la longueur de la mémoire tampon en cours, `GetBuffer` détruit la mémoire tampon en cours, il remplace une mémoire tampon de la taille demandée et réinitialise le décompte de références d’objet à zéro. Si vous avez précédemment appelé [LockBuffer](#lockbuffer) sur cette mémoire tampon, vous perdez le verrou de tampon.  
  
### <a name="return-value"></a>Valeur de retour  
 Un `PXSTR` pointeur vers la mémoire tampon de caractères de (se terminant par null) de l’objet.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour retourner le contenu de la mémoire tampon de la `CSimpleStringT` objet. Retourné `PXSTR` n’est pas une constante et par conséquent permet la modification directe de `CSimpleStringT` contenu.  
  
 Si vous utilisez le pointeur retourné par `GetBuffer` pour modifier le contenu de la chaîne, vous devez appeler [ReleaseBuffer](#releasebuffer) avant d’utiliser n’importe quel autre `CSimpleStringT` les méthodes membres.  
  
 L’adresse retournée par `GetBuffer` ne peut pas être valides après l’appel à `ReleaseBuffer` car supplémentaires `CSimpleStringT` opérations peuvent provoquer la `CSimpleStringT` mémoire tampon destinée à être réaffectées. La mémoire tampon n’est pas réaffectée si vous ne modifiez pas la longueur de la `CSimpleStringT`.  
  
 La mémoire tampon est automatiquement libérée lorsque la `CSimpleStringT` objet est détruit.  
  
 Si vous effectuer le suivi de la longueur de chaîne vous-même, vous ne devez pas ajouter le caractère null de fin. Toutefois, vous devez spécifier la longueur de la chaîne finale lorsque vous libérez la mémoire tampon avec `ReleaseBuffer`. Si vous n’ajoutez pas un caractère null de fin, vous devez passer la valeur -1 (valeur par défaut) pour la longueur. `ReleaseBuffer` Ensuite, détermine la longueur du tampon.  
  
 Si la mémoire est insuffisante pour satisfaire la `GetBuffer` demande, cette méthode lève une CMemoryException *.  
  
### <a name="example"></a>Exemple  
```cpp  
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();   
```
  
##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength  
Retourne un pointeur vers la mémoire tampon de caractères interne pour le `CSimpleStringT` objet, troncation ou augmente sa longueur si nécessaire pour correspondre exactement à la longueur spécifiée dans `nLength`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>Paramètres  
 `nLength`  
 La taille exacte de la `CSimpleStringT` mémoire tampon de caractères en caractères.  
  
### <a name="return-value"></a>Valeur de retour  
 A `PXSTR` pointeur vers la mémoire tampon de caractères de (se terminant par null) de l’objet.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer une longueur spécifiée de la mémoire tampon interne de la `CSimpleStringT` objet. Retourné `PXSTR` pointeur n’est pas `const` et vous permet ainsi la modification directe de `CSimpleStringT` contenu.  
  
 Si vous utilisez le pointeur retourné par [GetBufferSetLength](#getbuffersetlength) pour modifier le contenu de la chaîne, appelez `ReleaseBuffer` pour mettre à jour l’état interne de `CsimpleStringT` avant d’utiliser n’importe quel autre `CSimpleStringT` méthodes.  
  
 L’adresse retournée par `GetBufferSetLength` ne peut pas être valides après l’appel à `ReleaseBuffer` car supplémentaires `CSimpleStringT` opérations peuvent provoquer la `CSimpleStringT` mémoire tampon destinée à être réaffectées. La mémoire tampon n’est pas réaffectée si vous ne modifiez pas la longueur de la `CSimpleStringT`.  
  
 La mémoire tampon est automatiquement libérée lorsque la `CSimpleStringT` objet est détruit.  
  
 Si vous effectuer le suivi de la longueur de chaîne vous-même, n’ajoutez pas pas le caractère null de fin. Vous devez spécifier la longueur de la chaîne finale lorsque vous libérez la mémoire tampon à l’aide de `ReleaseBuffer`. Si vous ajoutez un caractère null de fin lorsque vous appelez `ReleaseBuffer`, passez -1 (valeur par défaut) pour la longueur à `ReleaseBuffer`, et `ReleaseBuffer` effectuera une `strlen` sur la mémoire tampon pour déterminer sa longueur.  
  
 Pour plus d’informations sur le comptage des références, consultez les articles suivants :  
  
- [Gérer la durée de vie des objets via le décompte](http://msdn.microsoft.com/library/windows/desktop/ms687260) dans le Kit de développement logiciel Windows. 
  
- [Implémentation d’un comptage de références](http://msdn.microsoft.com/library/windows/desktop/ms693431) dans le Kit de développement logiciel Windows.
  
- [Règles pour la gestion des décomptes de références](http://msdn.microsoft.com/library/windows/desktop/ms692481) dans le Kit de développement logiciel Windows.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::GetBufferSetLength`.  
  
```cpp  
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer() 
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```
  
##  <a name="getlength"></a>  CSimpleStringT::GetLength  
Retourne le nombre de caractères dans le `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>Valeur de retour  
 Nombre de caractères de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour retourner le nombre de caractères dans l’objet. Le nombre n’inclut pas un terminateur null.  
  
 Pour les jeux de caractères multioctets (MBCS), `GetLength` nombres chaque octet de caractère ; autrement dit, un responsable et de piste de 8 bits dans un caractère multioctet sont comptés comme deux octets. Consultez [FreeExtra](#freeextra) pour obtenir un exemple d’appel de cette fonction.  
  
##  <a name="getmanager"></a>  CSimpleStringT::GetManager  
Récupère le Gestionnaire de mémoire de le `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers le Gestionnaire de mémoire pour le `CSimpleStringT` objet.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer la mémoire utilisé par le Gestionnaire du `CSimpleStringT` objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets string, consultez [gestion de la mémoire et CStringT](../memory-management-with-cstringt.md).  
  
##  <a name="getstring"></a>  CSimpleStringT::GetString
Récupère la chaîne de caractères.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers une chaîne de caractères terminée par null.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer la chaîne de caractères associée à la `CSimpleStringT` objet.  
  
> [!NOTE]
>  Retourné `PCXSTR` pointeur est `const` et n’autorise pas la modification directe de `CSimpleStringT` contenu.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::GetString`.  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="isempty"></a>  CSimpleStringT::IsEmpty  
Tests un `CSimpleStringT` objet pour la condition vide.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>Valeur de retour  
 Retourne **true** si le `CSimpleStringT` objet a une longueur 0 ; sinon **false**.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour déterminer si l’objet contient une chaîne vide.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::IsEmpty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer  
Désactive le décompte de références et protège la chaîne dans la mémoire tampon.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur vers un `CSimpleStringT` objet ou une chaîne se terminant par null.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour verrouiller la mémoire tampon de la `CSimpleStringT` objet. En appelant `LockBuffer`, vous créez une copie de la chaîne, avec une valeur -1 pour le nombre de références. Lorsque la valeur du nombre de référence est -1, la chaîne dans la mémoire tampon est considéré comme étant dans un état « verrouillé ». Dans un état verrouillé, la chaîne est protégée de deux manières :  
  
-   Aucune autre chaîne ne peut obtenir une référence aux données dans la chaîne verrouillée, même si cette chaîne est assignée à la chaîne verrouillée.  
  
-   La chaîne verrouillée ne sera jamais référencer une autre chaîne, même si cette chaîne est copiée dans la chaîne verrouillée.  
  
 En verrouillant la chaîne dans la mémoire tampon, vous vérifiez que maintien exclusif de la chaîne de la mémoire tampon reste intacte.  
  
 Une fois que vous avez terminé avec `LockBuffer`, appelez [UnlockBuffer](#unlockbuffer) réinitialiser le nombre de références à 1.  
  
> [!NOTE]
>  Si vous appelez [GetBuffer](#getbuffer) sur une mémoire tampon verrouillée et que vous définissez la `GetBuffer` paramètre `nMinBufferLength` supérieure à la longueur de la mémoire tampon en cours, vous allez perdre le verrou de tampon. Un appel à `GetBuffer` détruit la mémoire tampon en cours, il remplace une mémoire tampon de la taille demandée et réinitialise le décompte de références à zéro.  
  
 Pour plus d’informations sur le comptage des références, consultez les articles suivants :  
  
- [Gérer la durée de vie des objets via le décompte](http://msdn.microsoft.com/library/windows/desktop/ms687260) dans le Kit de développement logiciel Windows  
  
- [Implémentation d’un comptage de références](http://msdn.microsoft.com/library/windows/desktop/ms693431) dans le Kit de développement logiciel Windows  
  
- [Règles pour la gestion des décomptes de références](http://msdn.microsoft.com/library/windows/desktop/ms692481) dans le Kit de développement logiciel Windows  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::LockBuffer`.  
  
```cpp  
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```
  
##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]  
Appelez cette fonction pour accéder à un caractère unique du tableau de caractères.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>Paramètres  
 `iChar`  
 Index de base zéro d’un caractère dans la chaîne.  
  
### <a name="remarks"></a>Notes  
 L’indice surchargé (`[]`) opérateur retourne un caractère spécifié par l’index de base zéro dans `iChar`. Cet opérateur est pratique pour remplacer le [GetAt](#getat) fonction membre.  
  
> [!NOTE]
>  Vous pouvez utiliser l’indice (`[]`) (opérateur) pour obtenir la valeur d’un caractère dans un `CSimpleStringT`, mais vous ne pouvez pas l’utiliser pour modifier la valeur d’un caractère dans un `CSimpleStringT`.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de **[] de CSimpleStringT::operator**.  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="operator_at"></a>  CSimpleStringT::operator \[\]
Appelez cette fonction pour accéder à un caractère unique du tableau de caractères.  
  
### <a name="syntax"></a>Syntaxe  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>Paramètres  
 `iChar`  
 Index de base zéro d’un caractère dans la chaîne.  
  
### <a name="remarks"></a>Notes  
 L’indice surchargé (`[]`) opérateur retourne un caractère spécifié par l’index de base zéro dans `iChar`. Cet opérateur est pratique pour remplacer le [GetAt](#getat) fonction membre.  
  
> [!NOTE]
>  Vous pouvez utiliser l’indice (`[]`) (opérateur) pour obtenir la valeur d’un caractère dans un `CSimpleStringT`, mais vous ne pouvez pas l’utiliser pour modifier la valeur d’un caractère dans un `CSimpleStringT`.  
  
  
##  <a name="operator_add_eq"></a>  CSimpleStringT::operator +=  
Joint une nouvelle chaîne ou un caractère à la fin d’une chaîne existante.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT& operator +=(PCXSTR pszSrc); 
CSimpleStringT& operator +=(const CSimpleStringT& strSrc); 
template<int t_nSize>  
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc); 
CSimpleStringT& operator +=(char ch); 
CSimpleStringT& operator +=(unsigned char ch); 
CSimpleStringT& operator +=(wchar_t ch);
```  
#### <a name="parameters"></a>Paramètres  
 `pszSrc`  
 Pointeur vers une chaîne se terminant par null.  
  
 `strSrc`  
 Un pointeur vers un existant `CSimpleStringT` objet.  
  
 *ch*  
 Caractère à ajouter.  
  
### <a name="remarks"></a>Notes  
 L’opérateur accepte un autre `CSimpleStringT` objet ou un caractère. Notez que la mémoire peuvent se produire lorsque vous utilisez cet opérateur de concaténation, car le nouveau stockage peut-être être alloué pour les caractères ajoutés à ce `CSimpleStringT` objet.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de **CSimpleStringT::operator +=**.  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="operator_eq"></a>  CSimpleStringT::operator =  
Affecte une nouvelle valeur à un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>Paramètres  
 `pszSrc`  
 Pointeur vers une chaîne se terminant par null.  
  
 `strSrc`  
 Un pointeur vers un existant `CSimpleStringT` objet.  
  
### <a name="remarks"></a>Notes  
 Si la chaîne de destination (le côté gauche) est déjà suffisamment grande pour stocker les nouvelles données, aucune nouvelle allocation de mémoire n’est effectuée. Notez que la mémoire peuvent se produire lorsque vous utilisez l’opérateur d’assignation, car le nouveau stockage est souvent alloué pour contenir la qui en résulte `CSimpleStringT` objet.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de **CSimpleStringT::operator =**.  
  
```cpp  
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;      
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```
  
##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR  

 Accède directement aux caractères stockés dans un `CSimpleStringT` objet comme une chaîne de style C.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>Valeur de retour  
 Un pointeur de caractère pour les données de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Aucuns caractères ne sont copiés ; seul un pointeur est retourné. Soyez prudent avec cet opérateur. Si vous modifiez un `CString` objet une fois que vous avez obtenu du pointeur de caractère, vous risquez de provoquer une réallocation de mémoire qui invalide le pointeur.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant illustre l’utilisation de **CSimpleStringT::operator PCXSTR**.  
  
```cpp  
// If the prototype of a function is known to the compiler, 
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype, 
// you must invoke the cast operator explicitly. For example, 
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and 
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will 
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;   
``` 
  
##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR
Pointeur vers une chaîne constante.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="preallocate"></a>  CSimpleStringT::Preallocate  
Alloue une quantité spécifique d’octets pour le `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>Paramètres  
 `nLength`  
 La taille exacte de la `CSimpleStringT` mémoire tampon de caractères en caractères.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour allouer une taille de mémoire tampon spécifique pour le `CSimpleStringT` objet.  
  
 `CSimpleStringT` génère un `STATUS_NO_MEMORY` exception s’il est impossible d’allouer de l’espace pour la mémoire tampon de caractères. Par défaut, l’allocation de mémoire est effectuée par les fonctions API WIN32 `HeapAlloc` ou `HeapReAlloc`.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::Preallocate`.  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="pxstr"></a>  CSimpleStringT::PXSTR  
Un pointeur vers une chaîne.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer  
Contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>Paramètres  
 `nNewLength`  
 Nouvelle longueur de la chaîne de caractères, sans compter un terminateur null. Si la chaîne est null terminé, la valeur par défaut de-1 définit la `CSimpleStringT` à la longueur actuelle de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour réallouer ou libérer la mémoire tampon de l’objet string. Si vous savez que la chaîne dans la mémoire tampon se termine par null, vous pouvez omettre le `nNewLength` argument. Si la chaîne n’est pas null terminée, utilisez `nNewLength` pour spécifier sa longueur. L’adresse retournée par [GetBuffer](#getbuffer) n’est pas valide après l’appel à `ReleaseBuffer` ou tout autre `CSimpleStringT` opération.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::ReleaseBuffer`.  
  
```cpp  
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

  // use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```
  
##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

Contrôle de la mémoire tampon allouée par [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>Paramètres  
 `nNewLength`  
 La longueur de la chaîne libérée  
  
### <a name="remarks"></a>Notes  
 Cette fonction est similaire à [ReleaseBuffer](#releasebuffer) , sauf qu’une longueur valide pour l’objet de chaîne doit être passée.  
  
##  <a name="setat"></a>  CSimpleStringT::SetAt  
Définit un seul caractère dans un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>Paramètres  
 `iChar`  
 Index de base zéro du caractère dans le `CSimpleStringT` objet. Le `iChar` paramètre doit être supérieur ou égal à 0 et inférieur à la valeur retournée par [GetLength](#getlength).  
  
 *ch*  
 Le caractère de nouvelle.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour remplacer le caractère situé à `iChar`. Cette méthode n’aboutira pas la chaîne si `iChar` dépasse les limites de la chaîne existante.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::SetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="setmanager"></a>  CSimpleStringT::SetManager  
Spécifie le Gestionnaire de mémoire de le `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>Paramètres  
 `pStringMgr`  
 Pointeur vers le nouveau gestionnaire de mémoire.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour spécifier une nouvelle mémoire utilisé par le Gestionnaire du `CSimpleStringT` objet. Pour plus d’informations sur les gestionnaires de mémoire et les objets string, consultez [gestion de la mémoire et CStringT](../memory-management-with-cstringt.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::SetManager`.  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="setstring"></a>  CSimpleStringT::SetString  
Définit la chaîne d’un `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Paramètres  
 `pszSrc`  
 Pointeur vers une chaîne se terminant par null.  
  
 `nLength`  
 Le nombre de caractères dans `pszSrc`.  
  
### <a name="remarks"></a>Notes  
 Copier une chaîne dans le `CSimpleStringT` objet. `SetString` remplace les données plus anciennes de la chaîne dans la mémoire tampon.  
  
 Les deux versions de `SetString` Vérifiez si `pszSrc` est un pointeur null et s’il s’agit, lèvent une **E_INVALIDARG** erreur.  
  
 La version d’un paramètre de `SetString` attend `pszSrc` pour pointer vers une chaîne se terminant par null.  
  
 La version de deux paramètres de `SetString` attend également `pszSrc` une chaîne se terminant par null. Il utilise `nLength` en tant que la longueur de chaîne, sauf si elle rencontre un terminateur null tout d’abord.  
  
 La version de deux paramètres de `SetString` vérifie également si `pszSrc` pointe vers un emplacement dans la mémoire tampon actuelle dans `CSimpleStringT`. Dans ce cas particulier, `SetString` utilise une fonction de copie de mémoire qui ne remplace pas les données de chaîne comme il copie les données de chaîne à sa mémoire tampon.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::SetString`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```
  
##  <a name="stringlength"></a>  CSimpleStringT::StringLength  
Retourne le nombre de caractères dans la chaîne spécifiée.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```  
#### <a name="parameters"></a>Paramètres  
 `psz`  
 Pointeur vers une chaîne se terminant par null.  
  
### <a name="return-value"></a>Valeur de retour  
 Le nombre de caractères dans `psz`; sans compter un terminateur null.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour récupérer le nombre de caractères dans la chaîne pointée par `psz`.  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::StringLength`.  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="truncate"></a>  CSimpleStringT::Truncate
Tronque la chaîne à la nouvelle longueur.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>Paramètres  
 `nNewLength`  
 Nouvelle longueur de la chaîne.  
  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour tronquer le contenu de la chaîne à la nouvelle longueur.  
  
> [!NOTE]
>  Cela n’affecte pas la durée allouée de la mémoire tampon. Pour réduire ou augmenter la mémoire tampon actuelle, consultez [FreeExtra](#freeextra) et [Preallocate](#preallocate).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant montre l'utilisation de `CSimpleStringT::Truncate`.  
  
```cpp  
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
``` 
  
##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer
 Déverrouille la mémoire tampon de la `CSimpleStringT` objet.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour réinitialiser le décompte de références de la chaîne à 1.  
  
 Le `CSimpleStringT` destructeur appelle automatiquement `UnlockBuffer` pour vous assurer que la mémoire tampon n’est pas verrouillée lorsque le destructeur est appelé. Pour obtenir un exemple de cette méthode, consultez [LockBuffer](#lockbuffer).  
  
##  <a name="dtor"></a>  CSimpleStringT :: ~ CSimpleStringT
Détruit un objet `CSimpleStringT`.  
  
### <a name="syntax"></a>Syntaxe  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>Notes  
 Appelez cette méthode pour détruire le `CSimpleStringT` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphique hiérarchique](../../mfc/hierarchy-chart.md)   
 [Classes de partagées ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)