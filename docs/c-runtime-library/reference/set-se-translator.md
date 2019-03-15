---
title: _set_se_translator
ms.date: 02/21/2018
apiname:
- _set_se_translator
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 18ee500d7b884d1934c29dc91d9bcb03d507680d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808376"
---
# <a name="setsetranslator"></a>_set_se_translator

Définissez une fonction de rappel par thread pour traduire les exceptions Win32 (exceptions structurées C) en code C++ des exceptions typées.

## <a name="syntax"></a>Syntaxe

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>Paramètres

*seTransFunction*<br/>
Pointeur vers une fonction de traduction d'exceptions structurées C que vous écrivez.

## <a name="return-value"></a>Valeur de retour

Retourne un pointeur vers la précédente fonction inscrite par **_set_se_translator**, de sorte que la fonction précédente peut être restaurée ultérieurement. Si aucune fonction précédente n’a été définie, la valeur de retour peut être utilisée pour restaurer le comportement par défaut ; Cette valeur peut être **nullptr**.

## <a name="remarks"></a>Notes

Le **_set_se_translator** fonction fournit un moyen pour gérer les exceptions Win32 (exceptions structurées C) en tant que C++ exceptions typées. Pour autoriser chaque exception C à être gérées par un C++ **catch** gestionnaire, définissez d’abord une classe de wrapper d’exception C qui peut être utilisée ou dérivée, pour attribuer un type de classe spécifique à une exception C. Pour utiliser cette classe, installez une fonction de traduction d'exception C personnalisée appelée par le mécanisme de gestion des exceptions interne chaque fois qu'une exception C est levée. Dans votre fonction de traduction, vous pouvez lever toute exception typée qui peut être interceptée par une correspondance C++ **catch** gestionnaire.

Vous devez utiliser [/EHa](../../build/reference/eh-exception-handling-model.md) lors de l’utilisation **_set_se_translator**.

Pour spécifier une fonction de traduction personnalisée, appelez **_set_se_translator** en utilisant le nom de votre fonction de traduction comme argument. La fonction de traduction que vous écrivez est appelée une fois pour chaque appel de fonction sur la pile a **essayez** blocs. Il n'existe aucune fonction de traduction par défaut.

Votre fonction de traduction se contente de lever une exception typée C++. Si elle effectue d'autres actions (écrire dans un fichier journal, par exemple), votre programme risque de ne pas se comporter comme prévu, car le nombre de fois où la fonction de traduction est appelée dépend de la plateforme.

Dans un environnement multithread, les fonctions de traduction sont gérées séparément pour chaque thread. Chaque nouveau thread doit installer sa propre fonction de traduction. Par conséquent, chaque thread est responsable de sa propre gestion de traduction. **_set_se_translator** est spécifique à un thread ; une autre DLL peut installer une fonction de traduction différente.

Le *seTransFunction* fonction que vous écrivez doit être compilé nativement (ne pas compilée avec/CLR). Il doit prendre un entier non signé et un pointeur vers un Win32 **_EXCEPTION_POINTERS** structure en tant qu’arguments. Les arguments sont des valeurs de retour des appels à l’API Win32 **GetExceptionCode** et **GetExceptionInformation** fonctions, respectivement.

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

Pour **_set_se_translator**, il existe des implications lors de la liaison dynamique vers le CRT ; une autre DLL dans le processus peut appeler **_set_se_translator** et remplacer votre gestionnaire avec sa propre.

Lorsque vous utilisez **_set_se_translator** à partir du code managé (code compilé avec/CLR) ou mixte du code natif et managé, n’oubliez pas que le traducteur affecte les exceptions générées en code natif uniquement. Les exceptions managées générées en code managé (par exemple, en déclenchant `System::Exception`) ne sont pas acheminées par le biais de la fonction de traduction. Les exceptions levées dans le code managé à l’aide de la fonction Win32 **RaiseException** ou provoquée par une exception de système comme une exception de division par zéro sont acheminées via le traducteur.

## <a name="requirements"></a>Spécifications

|Routine|En-tête requis|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

Pour plus d'informations sur la compatibilité, voir [Compatibilité](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Exemple

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception( unsigned int n ) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func(unsigned int u, EXCEPTION_POINTERS*)
{
    throw SE_Exception(u);
}

int main()
{
    auto original = _set_se_translator(trans_func);
    try
    {
        SEFunc();
    }
    catch(SE_Exception& e)
    {
        printf("Caught a __try exception, error %8.8x.\n", e.getSeNumber());
    }
    _set_se_translator(original);
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>Exemple

Bien que les fonctionnalités fournies par **_set_se_translator** est non disponible dans le code managé, il est possible d’utiliser ce mappage en code natif, même si ce code natif se trouve dans une compilation sous le **/CLR** basculer, tant que le code natif est indiqué à l’aide de `#pragma unmanaged`. Si une exception structurée est levée dans le code managé qui doit être mappé, le code qui génère et gère l’exception doit être marqué `#pragma unmanaged`. Le code suivant illustre une utilisation possible. Pour plus d’informations, consultez [Directives pragma et mot clé __Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md).

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <assert.h>
#include <stdio.h>
#include <exception>

int thrower_func(int i) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception {
private:
    unsigned int nSE;
public:
    SE_Exception() : nSE{ 0 } {}
    SE_Exception(unsigned int n) : nSE{ n } {}
    unsigned int getSeNumber() { return nSE; }
};

#pragma unmanaged
void my_trans_func(unsigned int u, PEXCEPTION_POINTERS)
{
    throw SE_Exception(u);
}

void DoTest()
{
    try
    {
        thrower_func(10);
    }
    catch(SE_Exception& e)
    {
        printf("Caught SE_Exception, error %8.8x\n", e.getSeNumber());
    }
    catch(...)
    {
        printf("Caught unexpected SEH exception.\n");
    }
}
#pragma managed

int main() {
    auto original = _set_se_translator(my_trans_func);
    DoTest();
    _set_se_translator(original);
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>Voir aussi

[Routines de gestion des exceptions](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
