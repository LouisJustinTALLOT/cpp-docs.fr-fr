---
title: 'TN059 : utilisation de macros de conversion MBCS/Unicode MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: d689e87b8f2804fe99804c6ca37a48bac01df263
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182731"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059 : utilisation des macros de conversion MBCS/Unicode MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note explique comment utiliser les macros de conversion MBCS/Unicode, qui sont définies dans AFXPRIV.H. Ces macros sont très utiles si votre application traite directement avec l'interface API OLE ou pour une raison quelconque, a souvent besoin de réaliser une conversion entre Unicode et MBCS.

## <a name="overview"></a>Vue d’ensemble

Dans MFC 3.x, une DLL spéciale a été utilisée (MFCANS32.DLL) pour effectuer une conversion automatique entre Unicode et MBCS lors de l'appel des interfaces OLE. Cette DLL est une couche quasiment transparente qui autorise l’accès en écriture pour les applications OLE, comme si les API et les interfaces OLE étaient de type MBCS, alors qu’elles sont toujours de type Unicode (sauf pour les ordinateurs Macintosh). Bien que cette couche s'avère pratique et permet la conversion rapide des applications Win16 en Win32 (les applications Microsoft MFC, Word, Excel et VBA utilisent cette technologie), elle a parfois un impact significatif sur les performances système. C'est pour cette raison que MFC 4.x n'utilise pas cette DLL mais communique directement avec les interfaces OLE Unicode. Pour cela, MFC doit effectuer une conversion Unicode/MBCS lors de l'appel à une interface OLE, et doit souvent effectuer une conversion Unicode en MBCS lors de l'implémentation d'une interface OLE. Pour réaliser les conversions efficacement et facilement, plusieurs macros ont été créées.

Un des plus grands obstacles dans la création d'un ensemble de macros est l'allocation de mémoire. Les chaînes ne pouvant pas être converties depuis leur emplacement, il est donc nécessaire d'allouer de la mémoire supplémentaire pour stocker les résultats de la conversion. L'opération peut être réalisée à l'aide d'un code semblable à celui-ci :

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

Cette méthode présente quelques inconvénients. Le problème majeur concerne la quantité importante de code à écrire, tester et déboguer. Le moindre appel de fonction est maintenant beaucoup plus complexe. De plus, cette procédure implique une importante surcharge d'exécution. La mémoire doit être allouée sur le tas et libérée chaque fois qu'une conversion est effectuée. Enfin, le code ci-dessus doit contenir les directives `#ifdefs` appropriées pour les versions Unicode et Macintosh (qui n'ont pas besoin de ce type de conversion).

Nous avons finalement choisi de créer des macros qui 1) masquent les différences entre les diverses plateformes, 2) utilisent une méthode d'allocation de mémoire efficace et 3) sont faciles à insérer dans le code source existant. Voici un exemple de l'une des définitions :

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

L'utilisation de cette macro au lieu du code ci-dessus simplifie beaucoup les choses :

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Il existe des appels supplémentaires lorsque la conversion est nécessaire, mais l'utilisation des macros est simple et efficace.

L'implémentation de chaque macro utilise la fonction _alloca() pour allouer de la mémoire provenant de la pile au lieu du tas. Il est beaucoup plus rapide d'allouer de la mémoire à partir de la pile plutôt que du tas, car elle est automatiquement libérée lorsque la fonction est désactivée. En outre, les macros évitent d’appeler `MultiByteToWideChar` (ou `WideCharToMultiByte` ) plus d’une fois. Cette opération s'effectue en allouant un peu plus de mémoire qu'il n'en faut. Nous savons qu’un MBC est converti en un seul **WCHAR** et que pour chaque **WCHAR** , nous aurons au maximum deux octets MBC. En allouant un peu plus de mémoire que nécessaire, mais toujours en quantité suffisante pour gérer la conversion du deuxième appel, le deuxième appel à la fonction de conversion est évité. L’appel à la fonction d’assistance `AfxA2Whelper` réduit le nombre de push d’arguments qui doivent être effectués pour effectuer la conversion (cela entraîne un code plus petit, que s’il est appelé `MultiByteToWideChar` directement).

Pour que les macros disposent d'un espace de stockage temporaire, il est nécessaire de déclarer une variable locale intitulée _convert qui effectue l'opération dans chaque fonction qui utilise les macros de conversion. Pour cela, la macro USES_CONVERSION doit être appelée comme indiqué précédemment dans l'exemple.

Il existe des macros de conversion génériques et des macros OLE spécifiques. Ces deux différents ensembles de macros sont décrits ci-dessous. Toutes les macros résident dans AFXPRIV.H.

## <a name="generic-conversion-macros"></a>Macros de conversion génériques

Les macros de conversion génériques forment le mécanisme sous-jacent. L'exemple de macro et son implémentation présentés dans la section précédente, A2W, concernent une macro "générique". Cette macro n'a pas de liaison OLE spécifique. L'ensemble des macros génériques est répertorié ci-dessous :

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

En plus des conversions de texte, il existe également des macros et des fonctions d'assistance permettant de convertir les chaînes `TEXTMETRIC`, `DEVMODE`, `BSTR` et les chaînes allouées par OLE. Ces macros n’entrent pas dans le cadre de cette discussion. pour plus d’informations, consultez AFXPRIV. H pour plus d’informations sur ces macros.

## <a name="ole-conversion-macros"></a>Macros de conversion OLE

Les macros de conversion OLE sont conçues spécifiquement pour gérer les fonctions qui attendent des caractères **OLESTR** . Si vous examinez les en-têtes OLE, vous verrez de nombreuses références à **LPCOLESTR** et **OLECHAR**. Ces types permettent de faire référence aux types de caractères utilisés dans les interfaces OLE d'une manière qui n'est pas spécifique à la plateforme. **OLECHAR** est mappé à **`char`** dans les plateformes Win16 et Macintosh et à **WCHAR** dans Win32.

Afin de limiter au minimum le nombre de directives de **#ifdef** dans le code MFC, nous avons une macro similaire pour chaque conversion dans laquelle les chaînes OLE sont impliquées. Les macros suivantes sont le plus souvent utilisées :

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Là encore, il existe des macros similaires pour exécuter des chaînes TEXTMETRIC, DEVMODE, BSTR et OLE allouées. Pour plus d'informations, consultez AFXPRIV.H.

## <a name="other-considerations"></a>Autres considérations

N'utilisez pas les macros dans une boucle étroite. Par exemple, vous ne souhaitez pas écrire le type de code suivant :

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Le code ci-dessus peut entraîner l'allocation de mégaoctets de mémoire sur la pile en fonction de la nature du contenu de la chaîne `lpsz`. Il faut également du temps pour convertir la chaîne de chaque itération de la boucle. Pour gagner du temps, déplacez ces conversions de constantes en dehors de la boucle :

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Si la chaîne n'est pas constante, encapsulez l'appel de la méthode au sein d'une fonction. Cela permet de libérer successivement de la mémoire tampon. Par exemple :

```cpp
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

Ne renvoyez jamais le résultat de l'une des macros, sauf si la valeur de renvoi implique de créer une copie des données avant le renvoi. Par exemple, ce code est incorrect :

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

Le code ci-dessus peut être corrigé en remplaçant la valeur de renvoi par un élément qui copie la valeur :

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

Les macros sont faciles à utiliser et à insérer dans votre code, mais il faut bien tenir compte des précautions d'utilisation mentionnées ci-dessus.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
