case "pin":
case "pinterest": {
  const axios = require("axios")
  const { getBuffer } = require("../../lib/utils")

  function pickRandom(arr = []) {
    return arr[Math.floor(Math.random() * arr.length)]
  }

  try {
    const query = text.trim()

    if (!query) {
      return sock.sendMessage(m.chat, {
        text: `_⚠️ Format Penggunaan:_\n\n💬 Contoh: *${prefix + command} kucing*`
      }, { quoted: m })
    }

    // react loading
    await sock.sendMessage(m.chat, {
      react: { text: "⏰", key: m.key }
    })

    const apiUrl = "https://api.nexray.web.id/search/pinterest?q=" + encodeURIComponent(query)

    const { data } = await axios.get(apiUrl)

    if (!data?.result?.length) {
      return sock.sendMessage(m.chat, {
        text: "❌ _Gambar tidak ditemukan_"
      }, { quoted: m })
    }

    const result = pickRandom(data.result)
    const buffer = await getBuffer(result)

    await sock.sendMessage(
      m.chat,
      {
        image: buffer,
        caption: `✅ ʜᴀsɪʟ ᴘᴇɴᴄᴀʀɪᴀɴ : *${query}*`
      },
      { quoted: m }
    )

  } catch (error) {
    await sock.sendMessage(
      m.chat,
      {
        text: `⚠️ Terjadi kesalahan.\n\nDetail Error:\n${error.message || error}`
      },
      { quoted: m }
    )
  }
}
break
