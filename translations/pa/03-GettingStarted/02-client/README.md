<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "a9c3ca25df37dbb4c1518174fc415ce1",
  "translation_date": "2025-05-17T09:35:36+00:00",
  "source_file": "03-GettingStarted/02-client/README.md",
  "language_code": "pa"
}
-->
# ਕਲਾਇੰਟ ਬਣਾਉਣਾ

ਕਲਾਇੰਟ ਉਹ ਕਸਟਮ ਐਪਲੀਕੇਸ਼ਨ ਜਾਂ ਸਕ੍ਰਿਪਟ ਹੁੰਦੇ ਹਨ ਜੋ ਸਿੱਧੇ MCP ਸਰਵਰ ਨਾਲ ਸੰਚਾਰ ਕਰਦੇ ਹਨ ਰਿਸੋਰਸ, ਟੂਲ ਅਤੇ ਪ੍ਰੋੰਪਟ ਦੀ ਬੇਨਤੀ ਕਰਨ ਲਈ। ਇੰਸਪੈਕਟਰ ਟੂਲ ਦੀ ਵਰਤੋਂ ਕਰਨ ਦੇ ਵਿਰੁੱਧ, ਜੋ ਸਰਵਰ ਨਾਲ ਸੰਚਾਰ ਕਰਨ ਲਈ ਗ੍ਰਾਫਿਕਲ ਇੰਟਰਫੇਸ ਪ੍ਰਦਾਨ ਕਰਦਾ ਹੈ, ਆਪਣਾ ਕਲਾਇੰਟ ਲਿਖਣ ਨਾਲ ਪ੍ਰੋਗਰਾਮੈਟਿਕ ਅਤੇ ਆਟੋਮੈਟਿਕ ਸੰਚਾਰ ਦੀ ਆਗਿਆ ਮਿਲਦੀ ਹੈ। ਇਹ ਵਿਕਾਸਕਾਰਾਂ ਨੂੰ ਆਪਣੇ ਕੰਮ ਦੇ ਵਹਾਅ ਵਿੱਚ MCP ਸਮਰੱਥਾਵਾਂ ਨੂੰ ਸ਼ਾਮਲ ਕਰਨ, ਕੰਮ ਆਟੋਮੇਟ ਕਰਨ, ਅਤੇ ਖਾਸ ਲੋੜਾਂ ਦੇ ਮੁਤਾਬਕ ਕਸਟਮ ਹੱਲ ਬਣਾਉਣ ਯੋਗ ਬਣਾਉਂਦਾ ਹੈ।

## ਝਲਕ

ਇਹ ਪਾਠ ਮਾਡਲ ਕੌਂਟੈਕਸਟ ਪ੍ਰੋਟੋਕੋਲ (MCP) ਇਕੋਸਿਸਟਮ ਦੇ ਅੰਦਰ ਕਲਾਇੰਟਾਂ ਦੇ ਸੰਕਲਪ ਨੂੰ ਪੇਸ਼ ਕਰਦਾ ਹੈ। ਤੁਸੀਂ ਸਿੱਖੋਗੇ ਕਿ ਕਿਵੇਂ ਆਪਣਾ ਕਲਾਇੰਟ ਲਿਖਣਾ ਹੈ ਅਤੇ ਇਸ ਨੂੰ MCP ਸਰਵਰ ਨਾਲ ਕਿਵੇਂ ਜੋੜਨਾ ਹੈ।

## ਸਿੱਖਣ ਦੇ ਉਦੇਸ਼

ਇਸ ਪਾਠ ਦੇ ਅੰਤ ਤੱਕ, ਤੁਸੀਂ ਇਹ ਕਰਨ ਦੇ ਯੋਗ ਹੋਵੋਗੇ:

- ਸਮਝੋ ਕਿ ਕਲਾਇੰਟ ਕੀ ਕਰ ਸਕਦਾ ਹੈ।
- ਆਪਣਾ ਕਲਾਇੰਟ ਲਿਖੋ।
- ਕਲਾਇੰਟ ਨੂੰ MCP ਸਰਵਰ ਨਾਲ ਕਨੈਕਟ ਕਰੋ ਅਤੇ ਟੈਸਟ ਕਰੋ ਤਾਂ ਜੋ ਇਹ ਯਕੀਨੀ ਬਣਾਇਆ ਜਾ ਸਕੇ ਕਿ ਇਹ ਉਮੀਦ ਦੇ ਅਨੁਸਾਰ ਕੰਮ ਕਰਦਾ ਹੈ।

## ਕਲਾਇੰਟ ਲਿਖਣ ਵਿੱਚ ਕੀ ਕੁਝ ਸ਼ਾਮਲ ਹੈ?

ਕਲਾਇੰਟ ਲਿਖਣ ਲਈ, ਤੁਹਾਨੂੰ ਇਹ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ:

- **ਸਹੀ ਲਾਇਬ੍ਰੇਰੀਆਂ ਨੂੰ ਇੰਪੋਰਟ ਕਰੋ**। ਤੁਸੀਂ ਪਹਿਲਾਂ ਦੀ ਤਰ੍ਹਾਂ ਹੀ ਲਾਇਬ੍ਰੇਰੀ ਦੀ ਵਰਤੋਂ ਕਰੋਗੇ, ਸਿਰਫ ਵੱਖਰੇ ਕੌਂਸਟ੍ਰਕਟਸ ਨਾਲ।
- **ਇੱਕ ਕਲਾਇੰਟ ਨੂੰ ਇੰਸਟੈਂਸ਼ੀਏਟ ਕਰੋ**। ਇਸ ਵਿੱਚ ਇੱਕ ਕਲਾਇੰਟ ਇੰਸਟੈਂਸ ਬਣਾਉਣਾ ਅਤੇ ਇਸਨੂੰ ਚੁਣੇ ਹੋਏ ਟ੍ਰਾਂਸਪੋਰਟ ਮੈਥਡ ਨਾਲ ਜੋੜਨਾ ਸ਼ਾਮਲ ਹੋਵੇਗਾ।
- **ਕੀ ਰਿਸੋਰਸ ਸੂਚੀਬੱਧ ਕਰਨੇ ਹਨ, ਇਸਦਾ ਫੈਸਲਾ ਕਰੋ**। ਤੁਹਾਡੇ MCP ਸਰਵਰ ਕੋਲ ਰਿਸੋਰਸ, ਟੂਲ ਅਤੇ ਪ੍ਰੋੰਪਟ ਹਨ, ਤੁਹਾਨੂੰ ਇਹ ਫੈਸਲਾ ਕਰਨ ਦੀ ਲੋੜ ਹੈ ਕਿ ਕਿਹੜਾ ਸੂਚੀਬੱਧ ਕਰਨਾ ਹੈ।
- **ਕਲਾਇੰਟ ਨੂੰ ਇੱਕ ਹੋਸਟ ਐਪਲੀਕੇਸ਼ਨ ਨਾਲ ਇੰਟੇਗਰੇਟ ਕਰੋ**। ਜਦੋਂ ਤੁਹਾਨੂੰ ਸਰਵਰ ਦੀਆਂ ਸਮਰੱਥਾਵਾਂ ਦਾ ਪਤਾ ਲੱਗ ਜਾਂਦਾ ਹੈ, ਤਾਂ ਤੁਹਾਨੂੰ ਇਸਨੂੰ ਆਪਣੇ ਹੋਸਟ ਐਪਲੀਕੇਸ਼ਨ ਵਿੱਚ ਸ਼ਾਮਲ ਕਰਨ ਦੀ ਲੋੜ ਹੈ ਤਾਂ ਜੋ ਜਦੋਂ ਕੋਈ ਯੂਜ਼ਰ ਕੋਈ ਪ੍ਰੋੰਪਟ ਜਾਂ ਹੋਰ ਕਮਾਂਡ ਟਾਈਪ ਕਰਦਾ ਹੈ ਤਾਂ ਉਸ ਦੇ ਅਨੁਸਾਰ ਸਰਵਰ ਫੀਚਰ ਚਲਾਇਆ ਜਾ ਸਕੇ।

ਹੁਣ ਜਦੋਂ ਕਿ ਅਸੀਂ ਉੱਚ ਪੱਧਰ ਤੇ ਸਮਝ ਗਏ ਹਾਂ ਕਿ ਅਸੀਂ ਕੀ ਕਰਨ ਜਾ ਰਹੇ ਹਾਂ, ਅਗਲੇ ਉਦਾਹਰਨ 'ਤੇ ਇੱਕ ਨਜ਼ਰ ਮਾਰਦੇ ਹਾਂ।

### ਇੱਕ ਉਦਾਹਰਨ ਕਲਾਇੰਟ

ਆਓ ਇਸ ਉਦਾਹਰਨ ਕਲਾਇੰਟ ਨੂੰ ਦੇਖੀਏ:
ਤੁਸੀਂ ਅਕਤੂਬਰ 2023 ਤੱਕ ਦੇ ਡੇਟਾ 'ਤੇ ਟ੍ਰੇਨ ਹੋ। 

ਉਪਰੋਕਤ ਕੋਡ ਵਿੱਚ ਅਸੀਂ:

- ਲਾਇਬ੍ਰੇਰੀਆਂ ਨੂੰ ਇੰਪੋਰਟ ਕਰਦੇ ਹਾਂ
- ਕਲਾਇੰਟ ਦਾ ਇੱਕ ਇੰਸਟੈਂਸ ਬਣਾਉਂਦੇ ਹਾਂ ਅਤੇ ਇਸਨੂੰ ਟ੍ਰਾਂਸਪੋਰਟ ਲਈ stdio ਦੀ ਵਰਤੋਂ ਕਰਦੇ ਹੋਏ ਜੋੜਦੇ ਹਾਂ।
- ਪ੍ਰੋੰਪਟ, ਰਿਸੋਰਸ ਅਤੇ ਟੂਲ ਸੂਚੀਬੱਧ ਕਰਦੇ ਹਾਂ ਅਤੇ ਉਨ੍ਹਾਂ ਨੂੰ ਸਾਰੇ ਨੂੰ ਚਲਾਉਂਦੇ ਹਾਂ।

ਇਹ ਲੋ, ਤੁਹਾਡੇ ਕੋਲ ਇੱਕ ਕਲਾਇੰਟ ਹੈ ਜੋ MCP ਸਰਵਰ ਨਾਲ ਗੱਲ ਕਰ ਸਕਦਾ ਹੈ।

ਅਗਲੇ ਕਸਰਤ ਭਾਗ ਵਿੱਚ ਆਪਣੇ ਸਮੇਂ ਨੂੰ ਲੈ ਕੇ ਹਰ ਕੋਡ ਸਨਿੱਪਟ ਨੂੰ ਵੱਖਰਾ ਕਰਦੇ ਹਾਂ ਅਤੇ ਸਮਝਾਉਂਦੇ ਹਾਂ ਕਿ ਕੀ ਹੋ ਰਿਹਾ ਹੈ।

## ਕਸਰਤ: ਕਲਾਇੰਟ ਲਿਖਣਾ

ਜਿਵੇਂ ਕਿ ਉੱਪਰ ਕਿਹਾ ਗਿਆ ਹੈ, ਚਲੋ ਆਪਣੇ ਸਮੇਂ ਨੂੰ ਲੈ ਕੇ ਕੋਡ ਨੂੰ ਸਮਝਾਈਏ, ਅਤੇ ਜੇ ਤੁਸੀਂ ਚਾਹੁੰਦੇ ਹੋ ਤਾਂ ਕੋਡ ਨਾਲ ਨਾਲ ਕਰੋ।

### -1- ਲਾਇਬ੍ਰੇਰੀਆਂ ਨੂੰ ਇੰਪੋਰਟ ਕਰੋ

ਆਓ ਲੋੜੀਂਦੀਆਂ ਲਾਇਬ੍ਰੇਰੀਆਂ ਨੂੰ ਇੰਪੋਰਟ ਕਰਦੇ ਹਾਂ, ਸਾਨੂੰ ਇੱਕ ਕਲਾਇੰਟ ਅਤੇ ਸਾਡੇ ਚੁਣੇ ਹੋਏ ਟ੍ਰਾਂਸਪੋਰਟ ਪ੍ਰੋਟੋਕੋਲ, stdio ਲਈ ਹਵਾਲੇ ਦੀ ਲੋੜ ਹੋਵੇਗੀ। stdio ਉਹਨਾਂ ਚੀਜ਼ਾਂ ਲਈ ਇੱਕ ਪ੍ਰੋਟੋਕੋਲ ਹੈ ਜੋ ਤੁਹਾਡੇ ਸਥਾਨਕ ਕੰਪਿਊਟਰ 'ਤੇ ਚੱਲਣ ਲਈ ਹੈ। SSE ਇੱਕ ਹੋਰ ਟ੍ਰਾਂਸਪੋਰਟ ਪ੍ਰੋਟੋਕੋਲ ਹੈ ਜੋ ਅਸੀਂ ਭਵਿੱਖ ਦੇ ਅਧਿਆਇਆਂ ਵਿੱਚ ਵਿਖਾਵਾਂਗੇ ਪਰ ਇਹ ਤੁਹਾਡਾ ਦੂਜਾ ਵਿਕਲਪ ਹੈ। ਫਿਲਹਾਲ, ਆਓ stdio ਨਾਲ ਜਾਰੀ ਰਹੀਏ।

ਆਓ ਇੰਸਟੈਂਸ਼ੀਏਸ਼ਨ 'ਤੇ ਅੱਗੇ ਵਧੀਏ।

### -2- ਕਲਾਇੰਟ ਅਤੇ ਟ੍ਰਾਂਸਪੋਰਟ ਨੂੰ ਇੰਸਟੈਂਸ਼ੀਏਟ ਕਰਨਾ

ਸਾਨੂੰ ਟ੍ਰਾਂਸਪੋਰਟ ਅਤੇ ਆਪਣੇ ਕਲਾਇੰਟ ਦਾ ਇੱਕ ਇੰਸਟੈਂਸ ਬਣਾਉਣ ਦੀ ਲੋੜ ਹੋਵੇਗੀ:

### -3- ਸਰਵਰ ਫੀਚਰ ਸੂਚੀਬੱਧ ਕਰਨਾ

ਹੁਣ, ਸਾਡੇ ਕੋਲ ਇੱਕ ਕਲਾਇੰਟ ਹੈ ਜੋ ਕਨੈਕਟ ਹੋ ਸਕਦਾ ਹੈ ਜੇਕਰ ਪ੍ਰੋਗਰਾਮ ਚਲਾਇਆ ਜਾਵੇ। ਹਾਲਾਂਕਿ, ਇਹ ਆਪਣੇ ਫੀਚਰਾਂ ਨੂੰ ਸੂਚੀਬੱਧ ਨਹੀਂ ਕਰਦਾ ਹੈ ਇਸ ਲਈ ਚਲੋ ਅਗਲਾ ਇਹ ਕਰੀਏ:

ਵਧੀਆ, ਹੁਣ ਅਸੀਂ ਸਾਰੇ ਫੀਚਰ ਕੈਪਚਰ ਕਰ ਲਏ ਹਨ। ਹੁਣ ਸਵਾਲ ਇਹ ਹੈ ਕਿ ਅਸੀਂ ਉਨ੍ਹਾਂ ਨੂੰ ਕਦੋਂ ਵਰਤਦੇ ਹਾਂ? ਖੈਰ, ਇਹ ਕਲਾਇੰਟ ਕਾਫ਼ੀ ਸਧਾਰਨ ਹੈ, ਸਧਾਰਨ ਇਸ ਮਾਇਨੇ ਵਿੱਚ ਕਿ ਜਦੋਂ ਅਸੀਂ ਉਨ੍ਹਾਂ ਨੂੰ ਚਾਹੁੰਦੇ ਹਾਂ ਤਾਂ ਸਾਨੂੰ ਫੀਚਰਾਂ ਨੂੰ ਸਪਸ਼ਟ ਤੌਰ 'ਤੇ ਕਾਲ ਕਰਨ ਦੀ ਲੋੜ ਹੋਵੇਗੀ। ਅਗਲੇ ਅਧਿਆਇ ਵਿੱਚ, ਅਸੀਂ ਇੱਕ ਹੋਰ ਉੱਚ-ਪੱਧਰੀ ਕਲਾਇੰਟ ਬਣਾਵਾਂਗੇ ਜਿਸ ਦੀ ਆਪਣੀ ਵੱਡੀ ਭਾਸ਼ਾ ਮਾਡਲ, LLM ਤੱਕ ਪਹੁੰਚ ਹੋਵੇਗੀ। ਫਿਲਹਾਲ, ਚਲੋ ਵੇਖੀਏ ਕਿ ਅਸੀਂ ਸਰਵਰ 'ਤੇ ਫੀਚਰਾਂ ਨੂੰ ਕਿਵੇਂ ਚਲਾਉਂਦੇ ਹਾਂ:

### -4- ਫੀਚਰਾਂ ਨੂੰ ਚਲਾਉਣਾ

ਫੀਚਰਾਂ ਨੂੰ ਚਲਾਉਣ ਲਈ ਸਾਨੂੰ ਯਕੀਨੀ ਬਣਾਉਣਾ ਹੈ ਕਿ ਅਸੀਂ ਸਹੀ ਦਲੀਲਾਂ ਅਤੇ ਕੁਝ ਮਾਮਲਿਆਂ ਵਿੱਚ ਉਸਦਾ ਨਾਮ ਜਿਸਨੂੰ ਅਸੀਂ ਚਲਾਉਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰ ਰਹੇ ਹਾਂ, ਨੂੰ ਦਰਸਾਇਆ ਹੈ।

### -5- ਕਲਾਇੰਟ ਚਲਾਉਣਾ

ਕਲਾਇੰਟ ਚਲਾਉਣ ਲਈ, ਟਰਮੀਨਲ ਵਿੱਚ ਹੇਠਾਂ ਦਿੱਤੇ ਕਮਾਂਡ ਨੂੰ ਟਾਈਪ ਕਰੋ:

## ਅਸਾਈਨਮੈਂਟ

ਇਸ ਅਸਾਈਨਮੈਂਟ ਵਿੱਚ, ਤੁਸੀਂ ਜੋ ਸਿੱਖਿਆ ਹੈ ਉਸ ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਇੱਕ ਕਲਾਇੰਟ ਬਣਾਉਣਗੇ ਪਰ ਆਪਣਾ ਕਲਾਇੰਟ ਬਣਾਉਣਗੇ।

ਇਹ ਇੱਕ ਸਰਵਰ ਹੈ ਜਿਸਨੂੰ ਤੁਸੀਂ ਆਪਣੇ ਕਲਾਇੰਟ ਕੋਡ ਰਾਹੀਂ ਕਾਲ ਕਰਨਾ ਹੈ, ਵੇਖੋ ਕਿ ਕੀ ਤੁਸੀਂ ਸਰਵਰ ਵਿੱਚ ਹੋਰ ਫੀਚਰ ਸ਼ਾਮਲ ਕਰ ਸਕਦੇ ਹੋ ਤਾਂ ਜੋ ਇਹ ਹੋਰ ਦਿਲਚਸਪ ਬਣ ਜਾਵੇ।

## ਹੱਲ

[ਹੱਲ](./solution/README.md)

## ਮੁੱਖ ਨਿਸ਼ਕਰਸ਼

ਇਸ ਅਧਿਆਇ ਲਈ ਮੁੱਖ ਨਿਸ਼ਕਰਸ਼ ਇਹ ਹਨ ਕਿ ਕਲਾਇੰਟਾਂ ਬਾਰੇ:

- ਸਰਵਰ 'ਤੇ ਫੀਚਰਾਂ ਦੀ ਖੋਜ ਅਤੇ ਚਲਾਉਣ ਦੋਵਾਂ ਲਈ ਵਰਤਿਆ ਜਾ ਸਕਦਾ ਹੈ।
- ਇੱਕ ਸਰਵਰ ਨੂੰ ਸ਼ੁਰੂ ਕਰ ਸਕਦਾ ਹੈ ਜਦੋਂ ਇਹ ਖੁਦ ਸ਼ੁਰੂ ਹੁੰਦਾ ਹੈ (ਜਿਵੇਂ ਕਿ ਇਸ ਅਧਿਆਇ ਵਿੱਚ) ਪਰ ਕਲਾਇੰਟ ਚੱਲ ਰਹੇ ਸਰਵਰਾਂ ਨਾਲ ਵੀ ਕਨੈਕਟ ਕਰ ਸਕਦੇ ਹਨ।
- ਸਰਵਰ ਦੀਆਂ ਸਮਰੱਥਾਵਾਂ ਦੀ ਜਾਂਚ ਕਰਨ ਦਾ ਇੱਕ ਵਧੀਆ ਤਰੀਕਾ ਹੈ ਇੰਸਪੈਕਟਰ ਵਰਗੇ ਵਿਕਲਪਾਂ ਦੇ ਨਾਲ ਜਿਵੇਂ ਕਿ ਪਿਛਲੇ ਅਧਿਆਇ ਵਿੱਚ ਵਰਣਨ ਕੀਤਾ ਗਿਆ ਸੀ।

## ਵਾਧੂ ਸਰੋਤ

- [MCP ਵਿੱਚ ਕਲਾਇੰਟ ਬਣਾਉਣਾ](https://modelcontextprotocol.io/quickstart/client)

## ਨਮੂਨੇ

- [ਜਾਵਾ ਕੈਲਕੂਲੇਟਰ](../samples/java/calculator/README.md)
- [.Net ਕੈਲਕੂਲੇਟਰ](../../../../03-GettingStarted/samples/csharp)
- [ਜਾਵਾਸਕ੍ਰਿਪਟ ਕੈਲਕੂਲੇਟਰ](../samples/javascript/README.md)
- [ਟਾਈਪਸਕ੍ਰਿਪਟ ਕੈਲਕੂਲੇਟਰ](../samples/typescript/README.md)
- [ਪਾਈਥਾਨ ਕੈਲਕੂਲੇਟਰ](../../../../03-GettingStarted/samples/python) 

## ਅਗਲਾ ਕੀ ਹੈ

- ਅਗਲਾ: [ਇੱਕ LLM ਦੇ ਨਾਲ ਕਲਾਇੰਟ ਬਣਾਉਣਾ](/03-GettingStarted/03-llm-client/README.md)

**ਅਸਵੀਕਰਤੀਕਰਨ**:  
ਇਹ ਦਸਤਾਵੇਜ਼ AI ਅਨੁਵਾਦ ਸੇਵਾ [Co-op Translator](https://github.com/Azure/co-op-translator) ਦੀ ਵਰਤੋਂ ਕਰਕੇ ਅਨੁਵਾਦ ਕੀਤਾ ਗਿਆ ਹੈ। ਜਦੋਂ ਕਿ ਅਸੀਂ ਸਹੀ ਹੋਣ ਦੀ ਕੋਸ਼ਿਸ਼ ਕਰਦੇ ਹਾਂ, ਕਿਰਪਾ ਕਰਕੇ ਧਿਆਨ ਦਿਓ ਕਿ ਸਵੈਚਾਲਿਤ ਅਨੁਵਾਦਾਂ ਵਿੱਚ ਗਲਤੀਆਂ ਜਾਂ ਅਸੁੱਠਤਾਵਾਂ ਹੋ ਸਕਦੀਆਂ ਹਨ। ਇਸਦੀ ਮੂਲ ਭਾਸ਼ਾ ਵਿੱਚ ਮੂਲ ਦਸਤਾਵੇਜ਼ ਨੂੰ ਪ੍ਰਮਾਣਿਕ ਸਰੋਤ ਮੰਨਿਆ ਜਾਣਾ ਚਾਹੀਦਾ ਹੈ। ਮਹੱਤਵਪੂਰਨ ਜਾਣਕਾਰੀ ਲਈ, ਪੇਸ਼ੇਵਰ ਮਨੁੱਖੀ ਅਨੁਵਾਦ ਦੀ ਸਿਫਾਰਸ਼ ਕੀਤੀ ਜਾਂਦੀ ਹੈ। ਇਸ ਅਨੁਵਾਦ ਦੀ ਵਰਤੋਂ ਤੋਂ ਪੈਦਾ ਹੋਈ ਕਿਸੇ ਵੀ ਗਲਤਫਹਿਮੀ ਜਾਂ ਗਲਤ ਵਿਆਖਿਆ ਲਈ ਅਸੀਂ ਜ਼ਿੰਮੇਵਾਰ ਨਹੀਂ ਹਾਂ।