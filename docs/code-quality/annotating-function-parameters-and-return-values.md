---
title: Annotation des paramètres de fonction et des valeurs de retour
description: Guide de référence pour les paramètres de fonction et les annotations de valeur de retour.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328011"
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotation des paramètres de fonction et des valeurs de retour

Cet article décrit les utilisations typiques d’annotations pour des paramètres de fonction simples — des scalars, et des pointeurs aux structures et aux classes — et la plupart des types de tampons. Cet article montre également des modèles d’utilisation courants pour les annotations. Pour des annotations supplémentaires qui sont liées à des fonctions, voir [le comportement de fonction annotant](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Paramètres de pointeur

Pour les annotations dans le tableau suivant, lorsqu’un paramètre de pointeur est annoté, l’analyseur signale une erreur si le pointeur est nul. Cette annotation s’applique aux pointeurs et à tout élément de données qui est pointé vers.

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_In_`

     Annote les paramètres d’entrée qui sont des scalars, des structures, des pointeurs aux structures et autres. Explicitement peut être utilisé sur des scalars simples. Le paramètre doit être valide en pré-état et ne sera pas modifié.

- `_Out_`

     Annote les paramètres de sortie qui sont des scalars, des structures, des pointeurs aux structures et autres. N’appliquez pas cette annotation à un objet qui ne peut pas retourner une valeur, par exemple, un scalaire qui est passé par la valeur. Le paramètre n’a pas besoin d’être valide en pré-état, mais doit être valide dans l’après-état.

- `_Inout_`

     Annote un paramètre qui sera modifié par la fonction. Il doit être valide à la fois dans le pré-état et après l’état, mais est supposé avoir des valeurs différentes avant et après l’appel. Doit s’appliquer à une valeur modifiable.

- `_In_z_`

     Un pointeur à une chaîne non terminée qui est utilisé comme entrée. La chaîne doit être valide en pré-état. Les variantes de `PSTR`, qui ont déjà les annotations correctes, sont préférées.

- `_Inout_z_`

     Un pointeur à un tableau de caractères annulé qui sera modifié. Il doit être valide avant et après l’appel, mais on suppose que la valeur a changé. Le terminateur nul peut être déplacé, mais seuls les éléments jusqu’au terminateur nul d’origine peuvent être consultés.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Un pointeur à un tableau, qui est lu par la fonction. Le tableau est `s` d’éléments de taille, qui doivent tous être valides.

     La `_bytes_` variante donne la taille dans les octets au lieu d’éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée comme des éléments. Par exemple, `char` les chaînes `_bytes_` n’utiliseraient la `wchar_t` variante que si une fonction similaire qui utilise le ferait.

- `_In_reads_z_(s)`

     Un pointeur à un tableau qui est annulé et a une taille connue. Les éléments jusqu’au terminateur nul, ou `s` s’il n’y a pas de terminateur nul, doivent être valides en pré-état. Si la taille est connue `s` dans les octets, échelle par la taille de l’élément.

- `_In_reads_or_z_(s)`

     Un pointeur à un tableau qui est annulé ou a une taille connue, ou les deux. Les éléments jusqu’au terminateur nul, ou `s` s’il n’y a pas de terminateur nul, doivent être valides en pré-état. Si la taille est connue `s` dans les octets, échelle par la taille de l’élément. (Utilisé pour `strn` la famille.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Un pointeur à `s` un tableau d’éléments (resp. octets) qui seront écrits par la fonction. Les éléments de tableau n’ont pas besoin d’être valides en pré-état, et le nombre d’éléments qui sont valides dans l’état post-état n’est pas spécifié. S’il y a des annotations sur le type de paramètre, elles sont appliquées dans l’après-état. Par exemple, prenons le code suivant.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     Dans cet exemple, l’appelant `size` fournit `p1`un tampon d’éléments pour . `MyStringCopy`rend certains de ces éléments valides. Plus important `_Null_terminated_` encore, l’annotation sur `PWSTR` les moyens qui `p1` est non-terminé dans l’après-état. De cette façon, le nombre d’éléments valides est encore bien défini, mais un nombre d’éléments spécifiques n’est pas nécessaire.

     La `_bytes_` variante donne la taille dans les octets au lieu d’éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée comme des éléments. Par exemple, `char` les chaînes `_bytes_` n’utiliseraient la `wchar_t` variante que si une fonction similaire qui utilise le ferait.

- `_Out_writes_z_(s)`

     Un pointeur à `s` un tableau d’éléments. Les éléments n’ont pas besoin d’être valides en pré-état. Dans l’après-État, les éléments jusqu’au terminateur nul, qui doit être présent, doivent être valides. Si la taille est connue `s` dans les octets, échelle par la taille de l’élément.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Un pointeur à un tableau, qui est à la fois lu et écrit dans la fonction. Il est d’éléments de taille, `s` et valide en pré-état et post-état.

     La `_bytes_` variante donne la taille dans les octets au lieu d’éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée comme des éléments. Par exemple, `char` les chaînes `_bytes_` n’utiliseraient la `wchar_t` variante que si une fonction similaire qui utilise le ferait.

- `_Inout_updates_z_(s)`

     Un pointeur à un tableau qui est nul-terminé et a une taille connue. Les éléments jusqu’au terminateur nul, qui doivent être présents, doivent être valides à la fois dans l’état pré-état et après l’état. La valeur dans l’état postérieur est présumée différente de la valeur dans le pré-État; qui comprend l’emplacement du terminateur nul. Si la taille est connue `s` dans les octets, échelle par la taille de l’élément.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Un pointeur à `s` un tableau d’éléments. Les éléments n’ont pas besoin d’être valides en pré-état. Dans l’après-État, les `c`éléments jusqu’à l’élément -e doivent être valides. La `_bytes_` variante peut être utilisée si la taille est connue dans les octets plutôt que le nombre d’éléments.

     Par exemple :

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Un pointeur à un tableau, qui est à la fois lu et écrit par la fonction. Il s’agit `s` d’éléments de taille, qui doivent `c` tous être valides en pré-état, et les éléments doivent être valides dans l’après-état.

     La `_bytes_` variante donne la taille dans les octets au lieu d’éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée comme des éléments. Par exemple, `char` les chaînes `_bytes_` n’utiliseraient la `wchar_t` variante que si une fonction similaire qui utilise le ferait.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Un pointeur à un tableau, qui est à `s` la fois lu et écrit par la fonction des éléments de taille. Défini comme équivalent à :

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     En d’autres termes, chaque élément qui `s` existe dans le tampon jusqu’à dans le pré-état est valide dans le pré-état et après l’état.

     La `_bytes_` variante donne la taille dans les octets au lieu d’éléments. Utilisez cette variante uniquement lorsque la taille ne peut pas être exprimée comme des éléments. Par exemple, `char` les chaînes `_bytes_` n’utiliseraient la `wchar_t` variante que si une fonction similaire qui utilise le ferait.

- `_In_reads_to_ptr_(p)`

     Un pointeur à `p - _Curr_` un tableau `p` pour `_Curr_`lequel (c’est-à-dire moins ) est une expression valable. Les éléments `p` avant doivent être valides en pré-état.

    Par exemple :

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Un pointeur à un tableau `p - _Curr_` annulé pour `p` lequel `_Curr_`l’expression (c’est-à-dire moins ) est une expression valide. Les éléments `p` avant doivent être valides en pré-état.

- `_Out_writes_to_ptr_(p)`

     Un pointeur à `p - _Curr_` un tableau `p` pour `_Curr_`lequel (c’est-à-dire moins ) est une expression valable. Les éléments `p` avant n’ont pas besoin d’être valides en pré-état et doivent être valides dans l’état post-état.

- `_Out_writes_to_ptr_z_(p)`

     Un pointeur à un tableau `p - _Curr_` annulé pour `p` `_Curr_`lequel (c’est-à-dire moins ) est une expression valide. Les éléments `p` avant n’ont pas besoin d’être valides en pré-état et doivent être valides dans l’état post-état.

## <a name="optional-pointer-parameters"></a>Paramètres de pointeur facultatifs

Lorsqu’une annotation `_opt_`de paramètre de pointeur inclut, elle indique que le paramètre peut être nul. Sinon, l’annotation se comporte de la même `_opt_`façon que la version qui n’inclut pas . Voici une liste `_opt_` des variantes des annotations de paramètres pointeurs :

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Paramètres de pointeur de sortie

Les paramètres de pointeur de sortie exigent une notation spéciale pour désambiguer l’annulation du paramètre et de l’emplacement pointé vers le haut.

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_Outptr_`

   Le paramètre ne peut pas être nul, et dans l’état post-état l’emplacement pointé vers l’autre ne peut pas être nul et doit être valide.

- `_Outptr_opt_`

   Le paramètre peut être nul, mais dans l’état post-état l’emplacement pointé vers l’autre ne peut pas être nul et doit être valide.

- `_Outptr_result_maybenull_`

   Le paramètre ne peut pas être nul, et dans l’état post-état l’emplacement pointé vers l’autre peut être nul.

- `_Outptr_opt_result_maybenull_`

   Le paramètre peut être nul, et dans l’état post-état l’emplacement pointé vers l’autre peut être nul.

  Dans le tableau suivant, d’autres sous-cordes sont insérées dans le nom de l’annotation pour qualifier davantage le sens de l’annotation. Les différents sous-cordes `_z` `_COM_`sont `_buffer_` `_bytebuffer_`, `_to_`, , , et .

> [!IMPORTANT]
> Si l’interface que vous annotez est COM, utilisez la forme COM de ces annotations. N’utilisez pas les annotations COM avec une autre interface de type.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Le pointeur `_Null_terminated_` retourné a l’annotation.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Le pointeur retourné a la sémantique COM, et porte donc une `_On_failure_` condition postérieure que le pointeur retourné est nul.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Le pointeur retourné indique un `s` tampon valide d’éléments ou d’octets de taille.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Le pointeur retourné indique `s` un tampon d’éléments de `c` taille ou d’octets, dont le premier est valide.

Certaines conventions d’interface présument que les paramètres de sortie sont annulés en cas d’échec. À l’exception du code COM explicite, les formulaires dans le tableau suivant sont préférés. Pour le code COM, utilisez les formulaires COM correspondants qui sont répertoriés dans la section précédente.

- `_Result_nullonfailure_`

   Modifie d’autres annotations. Le résultat est configuré à null si la fonction échoue.

- `_Result_zeroonfailure_`

   Modifie d’autres annotations. Le résultat est réglé à zéro si la fonction échoue.

- `_Outptr_result_nullonfailure_`

   Le pointeur retourné indique un tampon valide si la fonction réussit, ou nul si la fonction échoue. Cette annotation est pour un paramètre non facultatif.

- `_Outptr_opt_result_nullonfailure_`

   Le pointeur retourné indique un tampon valide si la fonction réussit, ou nul si la fonction échoue. Cette annotation est pour un paramètre facultatif.

- `_Outref_result_nullonfailure_`

   Le pointeur retourné indique un tampon valide si la fonction réussit, ou nul si la fonction échoue. Cette annotation est pour un paramètre de référence.

## <a name="output-reference-parameters"></a>Paramètres de référence de sortie

Une utilisation courante du paramètre de référence est pour les paramètres de sortie. Pour les paramètres simples `int&`de `_Out_` référence de sortie tels que , fournit la sémantique correcte. Cependant, lorsque la valeur de `int *&`sortie est un pointeur `_Outptr_ int **` tel que , les annotations pointeur équivalent comme ne fournissent pas la sémantique correcte. Pour exprimer de façon concise la sémantique des paramètres de référence de sortie pour les types de pointeurs, utilisez ces annotations composites :

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_Outref_`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul.

- `_Outref_result_maybenull_`

     Le résultat doit être valide dans l’après-État, mais peut être nul dans l’après-État.

- `_Outref_result_buffer_(s)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à tampon `s` valide des éléments de taille.

- `_Outref_result_bytebuffer_(s)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à tampon `s` valide de octets de taille.

- `_Outref_result_buffer_to_(s, c)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à `s` tampon d’éléments, `c` dont le premier est valide.

- `_Outref_result_bytebuffer_to_(s, c)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à `s` tampon des octets `c` dont le premier est valide.

- `_Outref_result_buffer_all_(s)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à tampon `s` valide de la taille des éléments valides.

- `_Outref_result_bytebuffer_all_(s)`

     Le résultat doit être valide dans l’après-état et ne peut pas être nul. Points à tampon `s` valide des octets d’éléments valides.

- `_Outref_result_buffer_maybenull_(s)`

     Le résultat doit être valide dans l’après-État, mais peut être nul dans l’après-État. Points à tampon `s` valide des éléments de taille.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Le résultat doit être valide dans l’après-État, mais peut être nul dans l’après-État. Points à tampon `s` valide de octets de taille.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Le résultat doit être valide dans l’après-État, mais peut être nul dans l’après-État. Points à `s` tampon d’éléments, `c` dont le premier est valide.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Le résultat doit être valide dans l’après-état, mais peut être nul dans l’état postérieur. Points à `s` tampon des octets `c` dont le premier est valide.

- `_Outref_result_buffer_all_maybenull_(s)`

     Le résultat doit être valide dans l’après-état, mais peut être nul dans l’état postérieur. Points à tampon `s` valide de la taille des éléments valides.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Le résultat doit être valide dans l’après-état, mais peut être nul dans l’état postérieur. Points à tampon `s` valide des octets d’éléments valides.

## <a name="return-values"></a>Valeurs retournées

La valeur de retour d’une fonction ressemble à un `_Out_` paramètre, mais est à un niveau différent de dé-référence, et vous n’avez pas à considérer le concept du pointeur pour le résultat. Pour les annotations suivantes, la valeur de retour est l’objet annoté , un échaudeur, un pointeur à une struction, ou un pointeur à un tampon. Ces annotations ont la même sémantique que l’annotation correspondante. `_Out_`

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Paramètres de chaîne de format

- `_Printf_format_string_`Indique que le paramètre est une `printf` chaîne de format pour une utilisation dans une expression.

     **Exemple**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Indique que le paramètre est une `scanf` chaîne de format pour une utilisation dans une expression.

     **Exemple**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Indique que le paramètre est une `scanf_s` chaîne de format pour une utilisation dans une expression.

     **Exemple**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Autres annotations courantes

### <a name="annotations-and-descriptions"></a>Annotations et descriptions

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Le paramètre, le champ ou le résultat `low` `hi`est dans la gamme (inclusive) de . L’équivalent de `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` cela est appliqué à l’objet annoté ainsi que les conditions appropriées avant ou post-état.

    > [!IMPORTANT]
    > Bien que les noms contiennent "in" et "out", la sémantique de `_In_` et `_Out_` ne s’appliquent **pas** à ces annotations.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     La valeur annotée `expr`est exactement . L’équivalent de `_Satisfies_(_Curr_ == expr)` cela est appliqué à l’objet annoté ainsi que les conditions appropriées avant ou post-état.

- `_Struct_size_bytes_(size)`

     S’applique à une déclaration de struct ou de classe. Indique qu’un objet valide de ce type peut être plus grand que `size`le type déclaré, avec le nombre d’octets donnés par . Par exemple :

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     La taille du tampon dans `pM` les `MyStruct *` octets d’un paramètre de type est alors prise pour être :

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Ressources associées

[Blog de l’équipe d’analyse de code](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)
- [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)
- [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
