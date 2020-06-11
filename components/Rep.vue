<template>
	<div class="representative" 
	:data-party="this.info.party" 
	:data-nnvote="this.info.nn_vote" 
	:data-surname="this.info.last_name" 
	:data-fullname="fullName" 
	:data-chamber="this.info.chamber" 
	:data-state="this.states[this.info.state]" 
	:data-gender="this.info.gender" 
	:data-age="age" 
	:data-nextelection="this.info.next_election" 
	:data-missedvotes="this.info.missed_votes_pct ? this.info.missed_votes_pct : 0" 
	:data-voteswithparty="this.info.votes_with_party_pct ? this.info.votes_with_party_pct : 0" 
	:data-votesagainstparty="this.info.votes_against_party_pct ? this.info.votes_against_party_pct : 0" 
	:data-donation="this.info.telecom_donation ? this.info.telecom_donation : 0" 
	data-hideprops="[]" 
	data-showage="true"
	data-showimage="true"
	data-shownextelection="true"
	data-showdonation="false"
	data-shownnvote="true"
	data-showinfobox="true"
	data-showvotepcts="true"
	data-showcontact="true"
	>
		<div class="rep-image-wrapper">
			<img src="" :data-lazysrc="`/img/reps/200/${this.info.id}_sm.jpg`" alt="" class="rep-image lazy">
		</div>
		<div class="info-box">
			<p class="name info-box-item" v-text="`${fullName}`"></p>
			<p class="party info-box-item" v-text="partyAndState"></p>
			<p class="age info-box-item" v-text="`${age} years old`"></p>
			<p class="election info-box-item" v-text="`Next Election: ${this.info.next_election}`"></p>
			<p class="donation info-box-item" v-text="donation"></p>
			<p class="nnvote info-box-item" :data-nnvote="this.info.nn_vote" v-html="`Net Neutrality? <span class='rep-vote'>${this.info.nn_vote}</span>`"></p>
			<p class="address info-box-item" v-if="this.info.office" v-text="this.info.office"></p>
			<!-- <p class="nnvote info-box-item" :data-nnvote="this.info.nn_vote" v-text="`Net Neutrality`"></p> -->
			<!-- <nuxt-link class="link info-box-item" :to="`/${this.info.id}`" target="_blank">Read More</nuxt-link> -->
		</div>
		<div class="percentages" v-if="this.info.votes_with_party_pct || this.info.votes_against_party_pct || this.info.missed_votes_pct">
			<div class="percentage" v-if="this.info.votes_with_party_pct">
				<p class="percentage-text">Votes With Party: {{ this.info.votes_with_party_pct }}%</p>
				<div class="percentage-fill">
					<div class="percentage-filler" :style="`width: ${this.info.votes_with_party_pct}%;`"></div>
				</div>
			</div>
			<!-- <div class="percentage" v-if="this.info.votes_against_party_pct">
				<p class="percentage-text">Votes Against Party: {{ this.info.votes_against_party_pct }}%</p>
				<div class="percentage-fill">
					<div class="percentage-filler" :style="`width: ${this.info.votes_against_party_pct}%;`"></div>
				</div>
			</div> -->
			<div class="percentage" v-if="this.info.missed_votes_pct">
				<p class="percentage-text">Missed Votes: {{ this.info.missed_votes_pct }}%</p>
				<div class="percentage-fill">
					<div class="percentage-filler" :style="`width: ${this.info.missed_votes_pct}%;`"></div>
				</div>
			</div>
		</div>
		<div class="contact">
			<div class="contact-row social">
				<a class="contact-method" v-if="this.info.wiki" data-method="wikipedia" :href="this.info.wiki" target="_blank">
					<img src="/icons/wikipedia.svg" alt="wikipedia" class="contact-method-icon">
				</a>
				<a class="contact-method" v-if="this.info.twitter_account" data-method="twitter" :href="`https://www.twitter.com/${this.info.twitter_account}`" target="_blank">
					<img src="/icons/twitter.svg" alt="twitter" class="contact-method-icon">
				</a>
				<a class="contact-method" v-if="this.info.youtube_account" data-method="youtube" :href="`https://www.youtube.com/${this.info.youtube_account}/videos`" target="_blank">
					<img src="/icons/youtube.svg" alt="youtube" class="contact-method-icon">
				</a>
				<a class="contact-method" v-if="this.info.facebook_account" data-method="facebook" :href="`https://www.facebook.com/${this.info.facebook_account}`" target="_blank">
					<img src="/icons/facebook.svg" alt="facebook" class="contact-method-icon">
				</a>
			</div>
			<div class="contact-row">
				<a class="contact-method" v-if="this.info.phone" data-method="phone" :href="`tel:+1-${this.info.phone}`">
					<img src="/icons/call.svg" alt="call" class="contact-method-icon"> {{ `1-${this.info.phone}` }}
				</a>
				<a class="contact-method" v-if="this.info.url" data-method="website" :href="this.info.url" v-text="`Website`" target="_blank"></a>
			</div>
			<!-- <div class="contact-row">
				<p class="contact-method office" v-if="this.info.office" v-text="this.info.office"></p>
			</div> -->
		</div>
	</div>
</template>

<script>
export default {
	name: 'Rep',
	props: {
		info: Object
	},
	data() {
		return {
			states: {
				AL: "Alabama",
				AK: "Alaska",
				AS: "American Samoa",
				AZ: "Arizona",
				AR: "Arkansas",
				CA: "California",
				CO: "Colorado",
				CT: "Connecticut",
				DE: "Delaware",
				DC: "District Of Columbia",
				FM: "Federated States Of Micronesia",
				FL: "Florida",
				GA: "Georgia",
				GU: "Guam",
				HI: "Hawaii",
				ID: "Idaho",
				IL: "Illinois",
				IN: "Indiana",
				IA: "Iowa",
				KS: "Kansas",
				KY: "Kentucky",
				LA: "Louisiana",
				ME: "Maine",
				MH: "Marshall Islands",
				MD: "Maryland",
				MA: "Massachusetts",
				MI: "Michigan",
				MN: "Minnesota",
				MS: "Mississippi",
				MO: "Missouri",
				MT: "Montana",
				NE: "Nebraska",
				NV: "Nevada",
				NH: "New Hampshire",
				NJ: "New Jersey",
				NM: "New Mexico",
				NY: "New York",
				NC: "North Carolina",
				ND: "North Dakota",
				MP: "Northern Mariana Islands",
				OH: "Ohio",
				OK: "Oklahoma",
				OR: "Oregon",
				PW: "Palau",
				PA: "Pennsylvania",
				PR: "Puerto Rico",
				RI: "Rhode Island",
				SC: "South Carolina",
				SD: "South Dakota",
				TN: "Tennessee",
				TX: "Texas",
				UT: "Utah",
				VT: "Vermont",
				VI: "Virgin Islands",
				VA: "Virginia",
				WA: "Washington",
				WV: "West Virginia",
				WI: "Wisconsin",
				WY: "Wyoming"
			}
		}
	},
	computed: {
		partyAndState: function() {
			let title = this.info.short_title.indexOf("Sen") > -1 ? "Senator" : this.info.short_title.indexOf("Rep") > -1 ? "Representative" : this.info.short_title.indexOf("Del") > -1 ? "Delegate" : this.info.short_title;
			let party = this.info.party == "R" ? "Republican" : this.info.party == "D" ? "Democratic" : (this.info.party == "I" || this.info.party == "ID") ? "Independent" : "";
			let state = this.states[this.info.state];
			return `${party} ${title} in ${state}`
		},
		fullName: function() {
			let fname = this.info.first_name;
			let lname = ` ${this.info.last_name}`;
			let middle = this.info.middle_name ? ` ${this.info.middle_name} ` : "";
			let suffix = this.info.suffix ? ` ${this.info.suffix}` : "";
			return `${fname}${middle}${lname}${suffix}`
		},
		donation: function() {
			let donation = this.info.telecom_donation ? `$${this.info.telecom_donation}` : "Unknown";
			return `Telecoms Donations: ${donation}`
		},
		age: function() {
			const moment = require('moment');
			const bday = moment(this.info.date_of_birth);
			const today = moment();
			return today.diff(bday, 'years')
		}
	}
}
</script>

<style lang="sass">
.representative
	flex: 1
	margin: 0.33rem
	// border: 0.1rem solid rgba(white, 0)
	min-width: 100%
	border-radius: 0.25rem
	animation: fadeIn 0.25s ease-in-out
	// background: #222
	background: var(--theme-itemWhite)
	// transition: border 0.25s ease-in-out
	box-shadow: var(--theme-boxShadow)
	@include flexCenter
	&:hover
		box-shadow: var(--theme-boxShadowHover)
		// border: 0.1rem solid rgba(white, 0.25)
	@media (min-width: 60rem)
		min-width: 40%
		max-width: 55%
	.rep-image-wrapper
		@include flexCenter
		margin: 0.5rem 0 0.5rem 0.5rem
		min-width: 160px
		min-height: 195px
		.rep-image
			box-sizing: content-box
			border: 0.25rem solid rgba(black, 0.25)
			border-radius: 0.25rem
	.info-box
		@include flexCenter
		flex: 1
		min-width: 50%
		// background: #333
		// background: var(--theme-whiteBG)
		margin: 0.5rem
		// border: 0.25rem solid rgba(black, 0.25)
		border-radius: 0.25rem
		overflow: hidden
		.info-box-item
			flex: 1
			padding: 0.25rem
			text-align: center
			min-width: 100%
			// background: #333
			@include flexCenter
			// color: white
			text-decoration: none
			@media (min-width: 32rem)
				font-size: 1.1rem
			&.nnvote
				&[data-nnvote="yes"]
					// border-right: 0.25rem solid rgba(green, 0.75)
					.rep-vote
						color: green
				&[data-nnvote="no"]
					.rep-vote
						color: red
					// border-right: 0.25rem solid rgba(red, 0.75)
				// &[data-nnvote="unknown"]
				// 	.rep-vote
				// 		color: red
					// border-right: 0.25rem solid rgba(#555, 0.75)
				.rep-vote
					margin-left: 0.5rem
			&.name
				font-size: 1.5rem
				padding: 1rem
			&.link
				justify-content: flex-end
		.wikipedia
			@include flexCenter
			text-decoration: none
			// color: white
			padding: 0.25rem
			width: 100%
			// transition: background 0.25s ease-in-out
		.netneutral
			@include flexCenter
			padding: 0.25rem
			width: 100%
			// transition: background 0.25s ease-in-out
	.percentages
		width: 100%
		@include flexCenter
		align-items: stretch
		margin: 0.25rem 0.5rem 0.5rem 0.5rem
		border-radius: 0.25rem
		// background: var(--theme-whiteBG)
		// background: #333
		.percentage
			flex: 1
			width: auto
			margin: 0.25rem
			border-radius: 0.25rem
			overflow: hidden
			box-shadow: var(--theme-boxShadowLight)
			@media (max-width: 75rem)
				min-width: 100%
			.percentage-text
				text-align: center
				font-size: 0.85rem
				background: var(--theme-itemWhite)
				// background: #444
				padding: 0.5rem
			.percentage-fill
				background: desaturate(red, 66)
				height: 1rem
				border-radius: 0.25rem
				overflow: hidden
				.percentage-filler
					height: 1rem
					background: desaturate(green, 66)
	.contact
		@include flexCenter
		align-items: stretch
		border-radius: 0.25rem
		overflow: hidden
		width: 100%
		margin: 0.25rem 0.5rem 0.5rem 0.5rem
		align-self: flex-end
		.contact-title
			min-width: 100%
			padding: 0.25rem
			text-align: center
			border: 0.05rem solid rgba(white, 0.5)
		.contact-row
			// min-width: 100%
			width: auto
			// flex: 1
			flex-grow: 1
			@include flexCenter
			flex-wrap: nowrap
			align-items: stretch
			// &.social
			@media (max-width: 30rem)
				min-width: 100%
			@media (max-width: 35rem)
				min-width: 40%
			.contact-method
				@include flexCenter
				width: auto
				flex: 1
				text-align: center
				white-space: nowrap
				// flex: 1
				// background: #333
				background: var(--theme-whiteBG)
				text-decoration: none
				// color: var(--theme-black)
				color: white
				padding: 0.5rem
				// transition: background 0.25s ease-in-out
				&:hover
					.contact-method-icon
						transform: scale(1.25)
				&[data-method="wikipedia"]
					background: darken(#FFFFFF, 5)
				&[data-method="twitter"]
					background: #1DA1F2
				&[data-method="youtube"]
					background: #FF0000
				&[data-method="facebook"]
					background: #3B5998
				&[data-method="website"]
					background: desaturate(#0077F8, 33)
					&:hover
						background: lighten(desaturate(#0077F8, 33), 5)
				&[data-method="phone"]
					background: desaturate(#00A651, 33)
					&:hover
						background: lighten(desaturate(#00A651, 33), 5)
					.contact-method-icon
						margin-right: 0.25rem
				&.office
					color: var(--theme-black)
				.contact-method-icon
					box-sizing: content-box
					margin: 0
					height: 1rem
					width: 1rem
					// transition: transform 0.1s ease-in-out
	&[data-showage="false"]
		.info-box
			.age
				display: none
	&[data-showimage="false"]
		.rep-image-wrapper
			display: none
	&[data-shownextelection="false"]
		.info-box
			.election
				display: none
	&[data-showdonation="false"]
		.info-box
			.donation
				display: none
	&[data-shownnvote="false"]
		.info-box
			.nnvote
				display: none
	&[data-showinfobox="false"]
		.info-box
			display: none
	&[data-showvotepcts="false"]
		.percentages
			display: none
	&[data-showcontact="false"]
		.contact
			display: none
</style>
