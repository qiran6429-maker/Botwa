const { default: makeWASocket, useMultiFileAuthState, DisconnectReason } = require('@whiskeysockets/baileys')
const pino = require('pino')
const axios = require('axios')
const fs = require('fs')

// NOMOR TETAP KAYAK PUNYA LU - AMAN GAK KE-DETECT
const NOMOR_BOT = process.env.NOMOR_BOT || '6285181423981'
const OWNER = process.env.OWNER || '6288276620224'
const SANDI = process.env.SANDI || 'aa121202'
// INI YANG BIKIN ERROR TADI, SEKARANG GUA HAPUS FALLBACK NYA
const GEMINI_API_KEY = process.env.GEMINI_API_KEY

const MENU_IMAGE_PATH = './menu.jpg'

let db = { antilink:{}, antilinkyt:{}, antilinkig:{}, antilinktiktok:{}, antilinkporno:{}, antilinkjudol:{}, antistiker:{}, antivirtex:{}, antispam:{}, welcome:{}, premium:{}, sewa:{} }
try { if(fs.existsSync('./db.json')) db = {...db,...JSON.parse(fs.readFileSync('./db.json'))} } catch(e){}
function saveDb(){ try{fs.writeFileSync('./db.json', JSON.stringify(db))}catch{} }

const MENU_UTAMA = `*🤖 AVRIBOT V9.8 FURINA - SUPPORT BUTTON*\n\nPilih menu di bawah bg 👇\nFitur 400+ | Fast | No ENC`

async function sendMenuButton(sock, from, msg){
  const buttons = [
    {buttonId: '.premiummenu', buttonText:{displayText:'💎 PREMIUM MENU'}, type:1},
    {buttonId: '.gamemenu', buttonText:{displayText:'🎮 GAME MENU'}, type:1},
    {buttonId: '.animemenu', buttonText:{displayText:'🌸 ANIME MENU'}, type:1},
    {buttonId: '.downloadmenu', buttonText:{displayText:'📥 DOWNLOAD'}, type:1},
    {buttonId: '.jagagroup '+SANDI, buttonText:{displayText:'🛡️ JAGA GROUP'}, type:1}
  ]
  try{
    if(fs.existsSync(MENU_IMAGE_PATH)){
      await sock.sendMessage(from, { image: fs.readFileSync(MENU_IMAGE_PATH), caption: MENU_UTAMA, footer: 'GB AVSTORE • No ENC 100%', buttons, headerType: 4 }, {quoted:msg})
    } else {
      await sock.sendMessage(from, { text: MENU_UTAMA, footer: 'GB AVSTORE', buttons, headerType: 1 }, {quoted:msg})
    }
  }catch{ await sock.sendMessage(from, {text:MENU_UTAMA}, {quoted:msg}) }
}

async function startBot(){
  const { state, saveCreds } = await useMultiFileAuthState('./session-avri')
  const sock = makeWASocket({ auth: state, printQRInTerminal:true, logger:pino({level:'silent'}) })
  if(!state.creds.registered){ setTimeout(async()=>{ try{ const code = await sock.requestPairingCode(NOMOR_BOT); console.log('KODE PAIRING:', code) }catch(e){console.log(e)} }, 3000) }
  sock.ev.on('creds.update', saveCreds)
  sock.ev.on('connection.update', u=>{ if(u.connection==='close' && u.lastDisconnect?.error?.output?.statusCode!==DisconnectReason.loggedOut) startBot() })
  sock.ev.on('messages.upsert', async m=>{
    const msg = m.messages[0]; if(!msg.message || msg.key.fromMe) return
    const from = msg.key.remoteJid
    let text = msg.message.conversation || msg.message.extendedTextMessage?.text || msg.message.buttonsResponseMessage?.selectedButtonId || ""
    const cmd = text.toLowerCase().trim()
    if(cmd==='.menu' || cmd==='menu'){ await sendMenuButton(sock,from,msg); return }
    if(cmd.startsWith('.brat')){
      let t = text.slice(5).trim()||'bambang'
      try{
        let buf=null
        const apis = [
          `https://api.siputzx.my.id/api/m/brat?text=${encodeURIComponent(t)}`,
          `https://api.ferdev.my.id/maker/brat?text=${encodeURIComponent(t)}`,
          `https://brat.caliphdev.com/api/brat?text=${encodeURIComponent(t)}`
        ]
        for(let api of apis){
          try{ const r=await axios.get(api,{responseType:'arraybuffer',timeout:15000}); if(r.headers['content-type'] && r.headers['content-type'].includes('json')) continue; if(r.data.byteLength>2000){ buf=Buffer.from(r.data); break; } }catch{}
        }
        if(!buf) throw 'fail'
        await sock.sendMessage(from,{image:buf,caption:`✅ brat: ${t}`},{quoted:msg})
      }catch{ await sock.sendMessage(from,{text:'Gagal brat'},{quoted:msg}) }
      return
    }
    if(cmd==='.premiummenu'){ await sock.sendMessage(from,{text:'*PREMIUM*\n.brat\n.qc\n.s\n.toanime'},{quoted:msg}); return }
  })
}
startBot()