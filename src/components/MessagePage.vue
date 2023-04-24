<template>
	<div class="container">
		<form class="message-form">
			<input type="text" class="typedMessage" placeholder="Enter Your Message.." autofocus>
			<button class="submit">Send</button>
		</form>
		<div class="messages"></div>
	</div>
</template>

<script>
export default {
	mounted() {
		let message = []
		
		function addMessage(text){
			const chat = {
				text,
				id: Date.now()
			}
			
			message.push(chat)
			
			const list = document.querySelector('.messages')
			list.insertAdjacentHTML('beforeend',
			`<p class="message-item" data-key="${chat.id}">
       <span>${chat.text}</span>`)
		}
		
		const form = document.querySelector('.message-form')
		form.addEventListener('submit', event => {
			event.preventDefault()
			
			const input = document.querySelector('.typedMessage')
			
			const text = input.value.trim()
			
			if (text !== ''){
				addMessage(text)
				input.value = ''
				input.focus()
			}
		})
		
	}
}
</script>