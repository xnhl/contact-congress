<template>
	<div id="sorter">
		<div id="options">
			<div id="options-toggle" class="options-section">
				<div class="options-section-title">Show:</div>
				<div class="options-box">
					<p class="options-box-title">Chamber</p>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Senate" data-toggleprop="senate" checked>
						<label class="option-check-label" for="Senate">Senate</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="House" data-toggleprop="house" checked>
						<label class="option-check-label" for="House">House</label>
					</div>
				</div>
				<div class="options-box">
					<p class="options-box-title">Party</p>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Republican" data-toggleprop="republican" checked>
						<label class="option-check-label" for="Republican">Rep</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Democrat" data-toggleprop="democrat" checked>
						<label class="option-check-label" for="Democrat">Dem</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Independent" data-toggleprop="independent" checked>
						<label class="option-check-label" for="Independent">Ind</label>
					</div>
				</div>
				<div class="options-box">
					<p class="options-box-title">Gender</p>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Male" data-toggleprop="male" checked>
						<label class="option-check-label" for="Male">Male</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Female" data-toggleprop="female" checked>
						<label class="option-check-label" for="Female">Female</label>
					</div>
				</div>
				<div class="options-box">
					<p class="options-box-title">Next Election</p>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="2020" data-toggleprop="twenty20" checked>
						<label class="option-check-label" for="2020">20</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="2022" data-toggleprop="twenty22" checked>
						<label class="option-check-label" for="2022">22</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="2024" data-toggleprop="twenty24" checked>
						<label class="option-check-label" for="2024">24</label>
					</div>
				</div>
				<div class="options-box">
					<p class="options-box-title">Net Neutrality</p>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Yes" data-toggleprop="yes" checked>
						<label class="option-check-label" for="Yes">Y</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="No" data-toggleprop="no" checked>
						<label class="option-check-label" for="No">N</label>
					</div>
					<div class="option">
						<input class="option-check" @change="optionToggle" type="checkbox" name="Unknown" data-toggleprop="unknown" checked>
						<label class="option-check-label" for="Unknown">?</label>
					</div>
				</div>
			</div>
			<div id="options-sort" class="options-section">
				<div class="options-section-title">Sort By:</div>
				<div class="options-box">
					<div class="option" @click="sortReps" data-sortprop="state">
						<p class="option-text">State</p>
					</div>
					<div class="option" @click="sortReps" data-sortprop="surname">
						<p class="option-text">Surname</p>
					</div>
					<div class="option" @click="sortReps" data-sortprop="age">
						<p class="option-text">Age</p>
					</div>
					<div class="option" @click="sortReps" data-sortprop="missedvotes">
						<p class="option-text">Missed Votes %</p>
					</div>
					<div class="option" @click="sortReps" data-sortprop="voteswithparty">
						<p class="option-text">Votes With Party %</p>
					</div>
				</div>
			</div>
			<div id="options-info" class="options-section">
				<div class="options-section-title">Show Information:</div>
				<div class="options-box">
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Image" data-infoprop="image" type="checkbox" checked>
						<label class="option-check-label" for="Image">Image</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Infobox" data-infoprop="infobox" type="checkbox" checked>
						<label class="option-check-label" for="Infobox">Main Info</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Age" data-infoprop="age" type="checkbox" checked>
						<label class="option-check-label" for="Age">Age</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Nextelection" data-infoprop="nextelection" type="checkbox" checked>
						<label class="option-check-label" for="Nextelection">Next Election</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Nnvote" data-infoprop="nnvote" type="checkbox" checked>
						<label class="option-check-label" for="Nnvote">Net Neutrality Vote</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Votepcts" data-infoprop="votepcts" type="checkbox" checked>
						<label class="option-check-label" for="Votepcts">Vote %s</label>
					</div>
					<div class="option">
						<input class="option-check" @change="infoToggle" name="Contact" data-infoprop="contact" type="checkbox" checked>
						<label class="option-check-label" for="Contact">Contact</label>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Sorter',
	data() {
		return {
			toggleProps: {
				republican: {
					count: 0,
					dataprop: "party",
					value: "R"
				},
				democrat: {
					count: 0,
					dataprop: "party",
					value: "D"
				},
				independent: {
					count: 0,
					dataprop: "party",
					value: "I"
				},
				male: {
					count: 0,
					dataprop: "gender",
					value: "M"
				},
				female: {
					count: 0,
					dataprop: "gender",
					value: "F"
				},
				senate: {
					count: 0,
					dataprop: "chamber",
					value: "Senate"
				},
				house: {
					count: 0,
					dataprop: "chamber",
					value: "House"
				},
				yes: {
					count: 0,
					dataprop: "nnvote",
					value: "yes"
				},
				no: {
					count: 0,
					dataprop: "nnvote",
					value: "no"
				},
				unknown: {
					count: 0,
					dataprop: "nnvote",
					value: "unknown"
				},
				twenty20: {
					count: 0,
					dataprop: "nextelection",
					value: "2020"
				},
				twenty22: {
					count: 0,
					dataprop: "nextelection",
					value: "2022"
				},
				twenty24: {
					count: 0,
					dataprop: "nextelection",
					value: "2024"
				}
			},
			infoProps: {
				age: true,
				image: true,
				nextelection: true,
				donation: false,
				nnvote: true,
				infobox: true,
				votepcts: true,
				contact: true
			},
			sortProps: {
				state: {count: 0},
				surname: {count: 0},
				age: {count: 1},
				donation: {count: 1},
				missedvotes: {count: 1},
				voteswithparty: {count: 1},
				votesagainstparty: {count: 1}
			}
		}
	},
	methods: {
		optionToggle: function(e) {
			let name = e.target.dataset.toggleprop;
			let tcount = this.toggleProps[name].count;
			let tdataprop = this.toggleProps[name].dataprop;
			let tvalue = this.toggleProps[name].value;
			if (tcount % 2 == 0) {
				let reps = [...document.getElementsByClassName("representative")];
				let repsLen = reps.length;
				for (let a = 0; a < repsLen; a++) {
					let hideProperties = JSON.parse(reps[a].dataset.hideprops);
					if (reps[a].dataset[tdataprop] == tvalue) {
						reps[a].classList.add("hide");
						hideProperties.push(tdataprop);
						reps[a].dataset.hideprops = JSON.stringify(hideProperties)
					}
				}
			} else {
				let reps = [...document.getElementsByClassName("representative")];
				let repsLen = reps.length;
				for (let a = 0; a < repsLen; a++) {
					let hideProperties = JSON.parse(reps[a].dataset.hideprops);
					if (reps[a].dataset[tdataprop] == tvalue) {
						hideProperties = hideProperties.filter(prop => prop !== tdataprop);
						reps[a].dataset.hideprops = JSON.stringify(hideProperties);
						if (!hideProperties.length) {
							reps[a].classList.remove("hide");
						}
					}
				}
			}
			this.toggleProps[name].count++
		},
		sortReps: function(e) {
			let reps = [...document.getElementsByClassName("representative")];
			let repsLen = reps.length;
			let propToSort = e.target.closest(".option").dataset.sortprop;
			let currentCount = this.sortProps[propToSort].count;
			let container = document.getElementById("reps-wrapper");
			let sorted;
			if (currentCount % 2 == 0) {
				sorted = reps.sort((a, b) => {
					let aa = a.dataset[propToSort];
					let bb = b.dataset[propToSort];
					let aSansPunc = aa.replace(",", "").replace(".", "");
					let bSansPunc = bb.replace(",", "").replace(".", "");
					if (aSansPunc.search(/[a-z]/gi) !== -1) {
						return aa < bb ? -1 : aa > bb ? 1 : 0
					} else {
						let aSansComma = aa.replace(",", "");
						let bSansComma = bb.replace(",", "");
						let newA = aa.indexOf(/\./g) > -1 ? parseFloat(aSansComma) : !aa.indexOf(/\./g) > -1 ? parseFloat(`${aSansComma}.00`) : null;
						let newB = bb.indexOf(/\./g) > -1 ? parseFloat(bSansComma) : !bb.indexOf(/\./g) > -1 ? parseFloat(`${bSansComma}.00`) : null;
						return newA == 0 ? 1 : aa < newB ? -1 : newA > newB ? 1 : 0
					}
				});
			} else {
				sorted = reps.sort((a, b) => {
					let aa = a.dataset[propToSort];
					let bb = b.dataset[propToSort];
					let aSansPunc = aa.replace(",", "").replace(".", "");
					let bSansPunc = bb.replace(",", "").replace(".", "");
					if (aSansPunc.search(/[a-z]/gi) !== -1) {
						return aa > bb ? -1 : aa < bb ? 1 : 0
					} else {
						let aSansComma = aa.replace(",", "");
						let bSansComma = bb.replace(",", "");
						let newA = aa.indexOf(/\./g) > -1 ? parseFloat(aSansComma) : !aa.indexOf(/\./g) > -1 ? parseFloat(`${aSansComma}.00`) : null;
						let newB = bb.indexOf(/\./g) > -1 ? parseFloat(bSansComma) : !bb.indexOf(/\./g) > -1 ? parseFloat(`${bSansComma}.00`) : null;
						return newA == 0 ? 1 : aa > newB ? -1 : newA < newB ? 1 : 0
					}
				});
			}
			for (let i = 0; i < repsLen; i++) {
				sorted[i].classList.add("lazyloading");
				if (i < 9) {
					sorted[i].classList.remove("lazyloading")
				}
				container.appendChild(sorted[i])
			}
			this.sortProps[propToSort].count++
		},
		infoToggle: function(e) {
			let reps = [...document.getElementsByClassName("representative")];
			let repsLen = reps.length;
			let propToSort = e.target.closest(".option-check").dataset.infoprop;
			let propName = `show${propToSort}`;
			if (this.infoProps[propToSort]) {
				for (let r = 0; r < repsLen; r++) {
					reps[r].dataset[propName] = false
				}
			} else {
				for (let r = 0; r < repsLen; r++) {
					reps[r].dataset[propName] = true
				}
			}
			this.infoProps[propToSort] = !this.infoProps[propToSort]
		}
	}
}
</script>

<style lang="sass">
#sorter
	flex: 1
	width: 100%
	margin: 0.5rem auto
	@include flexCenter
	border-radius: 0.25rem
	background: var(--theme-itemWhite)
	#options
		width: 100%
		padding: 0.25rem
		@include flexCenter
		#search-bar
			width: 100%
			padding: 0.25rem
			@include flexCenter
			#search-bar-input
				width: 100%
				max-width: 30rem
		.options-section
			@include flexCenter
			align-items: stretch
			width: auto
			flex-grow: 1
			margin: 0.25rem
			border-radius: 0.25rem
			box-shadow: $boxShadow
			&:first-child
				.options-box
					max-width: 55%
					box-shadow: var(--theme-boxShadowLight)
			.options-section-title
				width: 100%
				text-align: center
				padding: 0.25rem
				color: var(--theme-black)
			.options-box
				@include flexCenter
				align-items: stretch
				width: auto
				flex-grow: 1
				margin: 0.25rem
				border-radius: 0.25rem
				.options-box-title
					padding: 0.25rem
					text-align: center
					font-size: 0.75rem
					@include flexCenter
					color: var(--theme-black)
					width: 100%
				.option
					width: auto
					flex-grow: 1
					cursor: pointer
					padding: 0.25rem
					margin: 0.125rem
					box-shadow: var(--theme-boxShadowLight)
					border-radius: 0.25rem
					@include flexCenter
					.option-text
						cursor: pointer
						font-size: 0.75rem
						text-align: center
						color: var(--theme-black)
					.option-check
						cursor: pointer
						margin-right: 0.25rem
					.option-check-label
						cursor: pointer
						font-size: 0.75rem
</style>
